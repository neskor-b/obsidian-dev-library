---
type: code
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
title: "CSV-експорт фінансового звіту через SOLID"
aliases:
  - "SOLID CSV report export"
tags:
  - source-note
  - code
created: 2026-09-24
updated: 2026-09-24
source: "synthesis"
---

# CSV-експорт фінансового звіту через SOLID

## Фрагмент

Уявімо запит на фічу: система вміє показувати фінансовий звіт у web-інтерфейсі, і продуктова команда просить додати `CSV export`, щоб фінансовий відділ міг вивантажувати дані в Excel. Спершу фіксуємо policy: use case має "зібрати дані звіту і відрендерити їх у вибраному форматі".

```java showLineNumbers
public record ReportData(String title, BigDecimal revenue) {}

public record RenderedReport(
    String fileName,
    String contentType,
    byte[] content
) {}

public interface ReportDataGateway {
    ReportData loadReport(String reportId);
}

public interface ReportRenderer {
    RenderedReport render(ReportData data);
}

public interface ReportRendererRegistry {
    ReportRenderer forFormat(String format);
}

public interface GenerateFinancialReport {
    RenderedReport generate(String reportId, String format);
}

public interface PostgresClient {
    Row querySingle(String sql, String reportId);
}

public record Row(String title, BigDecimal revenue) {}

public final class FinancialReportInteractor implements GenerateFinancialReport {
    private final ReportDataGateway gateway;
    private final ReportRendererRegistry renderers;

    public FinancialReportInteractor(
        ReportDataGateway gateway,
        ReportRendererRegistry renderers
    ) {
        this.gateway = gateway;
        this.renderers = renderers;
    }

    @Override
    public RenderedReport generate(String reportId, String format) {
        ReportData data = gateway.loadReport(reportId);
        ReportRenderer renderer = renderers.forFormat(format);
        return renderer.render(data);
    }
}

public final class HtmlReportRenderer implements ReportRenderer {
    @Override
    public RenderedReport render(ReportData data) {
        return new RenderedReport("report.html", "text/html", renderHtml(data));
    }
}

public final class CsvReportRenderer implements ReportRenderer {
    @Override
    public RenderedReport render(ReportData data) {
        return new RenderedReport("report.csv", "text/csv", renderCsv(data));
    }
}

public final class PostgresReportDataGateway implements ReportDataGateway {
    private final PostgresClient postgres;

    public PostgresReportDataGateway(PostgresClient postgres) {
        this.postgres = postgres;
    }

    @Override
    public ReportData loadReport(String reportId) {
        Row row = postgres.querySingle(
            "select title, revenue from reports where id = ?",
            reportId
        );
        return new ReportData(row.title(), row.revenue());
    }
}

public final class InMemoryReportRendererRegistry implements ReportRendererRegistry {
    private final Map<String, ReportRenderer> renderers;

    public InMemoryReportRendererRegistry(Map<String, ReportRenderer> renderers) {
        this.renderers = renderers;
    }

    @Override
    public ReportRenderer forFormat(String format) {
        ReportRenderer renderer = renderers.get(format);

        if (renderer == null) {
            throw new IllegalArgumentException("Unsupported format: " + format);
        }

        return renderer;
    }
}

public final class ReportsController {
    private final GenerateFinancialReport generateFinancialReport;

    public ReportsController(GenerateFinancialReport generateFinancialReport) {
        this.generateFinancialReport = generateFinancialReport;
    }

    public HttpResponse download(String reportId, String format) {
        RenderedReport report = generateFinancialReport.generate(reportId, format);
        return HttpResponse.file(
            report.fileName(),
            report.contentType(),
            report.content()
        );
    }
}

public final class Application {
    public static void main(String[] args) {
        PostgresClient postgresClient = new RealPostgresClient();

        ReportDataGateway gateway =
            new PostgresReportDataGateway(postgresClient);

        ReportRenderer htmlRenderer = new HtmlReportRenderer();
        ReportRenderer csvRenderer = new CsvReportRenderer();

        ReportRendererRegistry registry =
            new InMemoryReportRendererRegistry(
                Map.of(
                    "html", htmlRenderer,
                    "csv", csvRenderer
                )
            );

        GenerateFinancialReport useCase =
            new FinancialReportInteractor(gateway, registry);

        ReportsController controller =
            new ReportsController(useCase);

        HttpResponse response = controller.download("report-42", "csv");

        sendToBrowser(response);
    }
}
```

^snippet

```mermaid
sequenceDiagram
    autonumber
    actor Client as Browser or Client
    participant Controller as ReportsController
    participant Interactor as FinancialReportInteractor
    participant Gateway as ReportDataGateway
    participant Registry as ReportRendererRegistry
    participant Renderer as CsvReportRenderer

    Note over Controller: HTTP adapter. Uses GenerateFinancialReport.
    Note over Interactor: Use case orchestrator. Uses Gateway and Registry.
    Note over Registry: Chooses concrete renderer by format.
    Note over Renderer: One concrete ReportRenderer implementation.

    Client->>Controller: GET /reports/{id}?format=csv
    Controller->>Interactor: generate(reportId, "csv")
    Interactor->>Gateway: loadReport(reportId)
    Gateway-->>Interactor: ReportData
    Interactor->>Registry: forFormat("csv")
    Registry-->>Interactor: CsvReportRenderer
    Interactor->>Renderer: render(reportData)
    Renderer-->>Interactor: RenderedReport("report.csv", "text/csv", bytes)
    Interactor-->>Controller: RenderedReport
    Controller->>Controller: HttpResponse.file(fileName, contentType, content)
    Controller-->>Client: HTTP response with file download
```

## Пояснення

Зверху оголошені контракти (`ReportDataGateway`, `ReportRenderer`, `ReportRendererRegistry`, `GenerateFinancialReport`), нижче йдуть concrete-реалізації, а в самому кінці `Application` збирає все докупи. Кожен принцип проявляється так:

- `SRP`: `FinancialReportInteractor` оркеструє use case, `PostgresReportDataGateway` читає дані, `CsvReportRenderer` відповідає за формат, а `ReportsController` за HTTP. У кожного модуля свій актор змін.
- `OCP`: щоб додати `XLSX`-експорт, ми створюємо `XlsxReportRenderer` і реєструємо його на периферії. Ядро use case не треба переписувати.
- `LSP`: `HtmlReportRenderer`, `CsvReportRenderer` і майбутній `XlsxReportRenderer` повертають один і той самий контракт `RenderedReport`. Клієнт не повинен знати, який саме renderer стоїть за цим.
- `ISP`: `ReportsController` залежить від вузького `GenerateFinancialReport`, а не від товстого `ReportsService`, де поруч живуть `deleteReport`, `reindexReports` та інші непотрібні операції.
- `DIP`: interactor залежить від `ReportDataGateway` і `ReportRendererRegistry`, а не від `PostgresClient` чи конкретного CSV-класу. Concrete wiring живе в composition root.

Коли приходить наступна вимога ("додайте ще XLSX export"): додаємо `XlsxReportRenderer implements ReportRenderer`, реєструємо його в `ReportRendererRegistry`, додаємо тести, що `GenerateFinancialReport` однаково працює з `html`, `csv` і `xlsx` — і не чіпаємо `FinancialReportInteractor`.

## Ризики або smells

- Поганий перший імпульс на цю ж фічу — один клас `ReportsService` з `if (format.equals("csv"))` поруч із `deleteReport()` і `reindexReports()` — змішує читання з Postgres, вибір формату, HTTP-відповідь, аудит експорту й admin-методи в одному місці.
- Такий код "здається швидким", але саме він робить наступний формат дорожчим за попередній: підміна реалізації вимагає редагувати той самий `if/else`-ланцюг, ризикуючи зачепити вже працюючі формати.

## Пов'язані концепти

- [[02-Concepts/single-responsibility-means-one-actor|SRP означає одного актора, а не одну дію]]
- [[02-Concepts/open-closed-protects-high-level-policy|OCP захищає high-level policy через ієрархію залежностей]]
- [[02-Concepts/liskov-substitution-preserves-client-behavior|LSP зберігає поведінку клієнта при підстановці]]
- [[02-Concepts/interface-segregation-avoids-dependencies-on-unused-operations|ISP ізолює клієнтів від невикористаних операцій]]
- [[02-Concepts/dependency-inversion|Інверсія залежностей]]
- [[03-Maps/solid-and-clean-architecture-principles|SOLID та принципи Clean Architecture]]

## Пов'язані source notes

- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle|Розділ 7. Принцип єдиної відповідальності]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-11-dependency-inversion-principle|Розділ 11. Принцип інверсії залежностей]]
- [[04-Playbooks/playbook-solid-in-code|Як дотримуватись SOLID у коді]]
