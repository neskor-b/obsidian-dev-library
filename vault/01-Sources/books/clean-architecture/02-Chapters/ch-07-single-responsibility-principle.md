---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "7"
title: "Принцип єдиної відповідальності"
aliases:
  - "Single Responsibility Principle"
  - "SRP"
tags:
  - source-note
  - chapter
created: 2026-04-14
updated: 2026-04-18
source: "excerpt"
---

# Принцип єдиної відповідальності

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 7
- Тип джерела: уривок

## Головна ідея

У цьому розділі Роберт Мартін уточнює найпоширеніше непорозуміння навколо `SRP`: йдеться не про те, що модуль має робити лише "одну річ", а про те, що він має бути відповідальним перед одним актором, тобто перед однією узгодженою причиною для зміни. Коли в одному модулі зібрано поведінку для різних акторів, зміни починають протікати між командами через випадкову спільну логіку, конфліктні merge-и й розмиті межі відповідальності.

^clean-architecture-ch07-main-idea

## Ключові тези

- `SRP` не слід плутати з правилом "function should do one thing"; це окрема, нижчорівнева дисципліна для малих функцій, а не принцип модульного дизайну. ^clean-architecture-ch07-thesis-not-one-thing
- Класичне формулювання `SRP` як "one reason to change" точніше читати через організаційний сенс: модуль має відповідати одному актору, а не кільком незалежним групам запиту на зміни. ^clean-architecture-ch07-thesis-one-actor
- `Module` у цьому контексті означає не лише source file, а будь-який cohesive набір функцій і даних; сама ідея cohesion уже передбачає прив'язку до одного актора. ^clean-architecture-ch07-thesis-cohesion
- Приклад `Employee` з методами `calculatePay()`, `reportHours()` і `save()` порушує `SRP`, бо одночасно обслуговує фінансового, операційного й технічного акторів: `CFO`, `COO` і `CTO`. ^clean-architecture-ch07-thesis-employee-actors
- Один із симптомів порушення `SRP` - accidental duplication: спільна helper-функція на кшталт `regularHours()` здається повторним використанням, але насправді склеює різні бізнес-значення й дозволяє зміні для `payroll` зламати `HR`-звітність. ^clean-architecture-ch07-thesis-accidental-duplication
- Другий симптом - risky merges: коли різні команди змінюють один і той самий файл з різних причин, сам файл стає точкою організаційного конфлікту. ^clean-architecture-ch07-thesis-merges
- Типове рішення полягає в тому, щоб розвести actor-specific поведінку в окремі класи навколо спільного `EmployeeData`, а зручний публічний API за потреби відновити через `Facade`. ^clean-architecture-ch07-thesis-solutions

## Опорні схеми

- Figure 7.1: клас `Employee` показано як спільну точку залежності для `CFO`, `COO` і `CTO`; це візуалізація кількох акторів в одному модулі. ^clean-architecture-ch07-figure-employee
- Figure 7.2: `calculatePay()` і `reportHours()` з'єднані через `regularHours`; схема підкреслює, як технічно спільний алгоритм може означати бізнесово різні правила. ^clean-architecture-ch07-figure-regular-hours
- Figure 7.3: `PayCalculator`, `HourReporter` і `EmployeeSaver` працюють через `EmployeeData`, але не знають один про одного; це базове структурне розв'язання `SRP`. ^clean-architecture-ch07-figure-split
- Figure 7.4: `EmployeeFacade` повертає зручний вхідний інтерфейс, не відновлюючи стару змішаність відповідальностей. ^clean-architecture-ch07-figure-facade
- Figure 7.5: компромісний варіант залишає найважливіший бізнес-метод у `Employee`, а слабші функції делегує окремим сервісам. ^clean-architecture-ch07-figure-hybrid

## Практичні правила

- Визначай межу модуля через актора або групу узгоджених змін, а не через поверхове "це все про employee".
- Якщо один файл регулярно змінюють різні команди з різних причин, це сигнал хибної cohesion.
- Не поспішай виносити "спільний" helper, якщо однакова формула обслуговує різні бізнес-смисли; інколи розділення без повторного використання безпечніше.
- Після розділення відповідальностей зберігай зручність клієнтського API через `Facade`, а не через повернення до змішаного модуля.

## Розгорнутий приклад

### Фрагмент 1: порушення `SRP`

```java showLineNumbers
public final class Employee {
    private final EmployeeRecord record;

    public Employee(EmployeeRecord record) {
        this.record = record;
    }

    public Money calculatePay() {
        return regularPayHours() * record.hourlyRate();
    }

    public HoursReport reportHours() {
        return new HoursReport(record.id(), regularPayHours(), record.overtimeHours());
    }

    public void save(EmployeeGateway gateway) {
        gateway.save(record);
    }

    private int regularPayHours() {
        return Math.min(record.totalHours(), 40);
    }
}
```

^clean-architecture-ch07-code-employee-violation

### Фрагмент 2: розділення за акторами

```java showLineNumbers
public record EmployeeData(
    String id,
    int totalHours,
    int overtimeHours,
    Money hourlyRate
) {}

public final class PayCalculator {
    public Money calculatePay(EmployeeData data) {
        return regularPayrollHours(data) * data.hourlyRate();
    }

    private int regularPayrollHours(EmployeeData data) {
        return Math.min(data.totalHours(), 40);
    }
}

public final class HourReporter {
    public HoursReport reportHours(EmployeeData data) {
        return new HoursReport(data.id(), regularReportHours(data), data.overtimeHours());
    }

    private int regularReportHours(EmployeeData data) {
        return data.totalHours();
    }
}

public final class EmployeeSaver {
    private final EmployeeGateway gateway;

    public EmployeeSaver(EmployeeGateway gateway) {
        this.gateway = gateway;
    }

    public void saveEmployee(EmployeeData data) {
        gateway.save(data);
    }
}
```

^clean-architecture-ch07-code-employee-split

### Фрагмент 3: фасад після розділення

```java showLineNumbers
public final class EmployeeFacade {
    private final PayCalculator payCalculator;
    private final HourReporter hourReporter;
    private final EmployeeSaver employeeSaver;

    public EmployeeFacade(
        PayCalculator payCalculator,
        HourReporter hourReporter,
        EmployeeSaver employeeSaver
    ) {
        this.payCalculator = payCalculator;
        this.hourReporter = hourReporter;
        this.employeeSaver = employeeSaver;
    }

    public Money calculatePay(EmployeeData data) {
        return payCalculator.calculatePay(data);
    }

    public HoursReport reportHours(EmployeeData data) {
        return hourReporter.reportHours(data);
    }

    public void save(EmployeeData data) {
        employeeSaver.saveEmployee(data);
    }
}
```

^clean-architecture-ch07-code-employee-facade

Перший фрагмент показує типове порушення `SRP`: один клас виглядає природним через назву `Employee`, але фактично обслуговує трьох різних акторів. Саме тому helper `regularPayHours()` стає небезпечним місцем випадкової спільності: для `payroll` і для `hours report` може знадобитися різна логіка, навіть якщо спочатку формула виглядає однаково.

Другий фрагмент розводить поведінку за акторами. `PayCalculator`, `HourReporter` і `EmployeeSaver` читають одні й ті самі дані, але не знають один про одного і можуть змінюватися незалежно. Це не "забагато класів", а нормальна ціна за те, що зміна для `CFO` не протікає в `HR` чи `DBA`-сценарій.

Третій фрагмент повертає ergonomic API через `Facade`. Клієнтський код усе ще може працювати з одним входом, але модульна межа вже проведена правильно: фасад лише делегує, а не змішує різні причини для зміни в одному алгоритмічному тілі.

## Важливі цитати

> A module should be responsible to one, and only one, actor.

^clean-architecture-ch07-quote-actor

> Cohesion is the force that binds together the code responsible to a single actor.

^clean-architecture-ch07-quote-cohesion

## Пов'язані концепти

- [[02-Concepts/single-responsibility-means-one-actor|SRP означає одного актора, а не одну дію]]
- [[03-Maps/solid-and-clean-architecture-principles|SOLID організовує модулі для змінюваності]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles|Попередній вузол: Принципи дизайну (SOLID)]]

## Пов'язані нотатки

- [[02-Concepts/single-responsibility-means-one-actor#^single-responsibility-means-one-actor-definition|Спільний концепт про одного актора як справжній сенс SRP]]
- [[03-Maps/solid-and-clean-architecture-principles#^solid-organizes-modules-for-change-definition|Оглядова нотатка про роль SOLID у mid-level дизайні]]
