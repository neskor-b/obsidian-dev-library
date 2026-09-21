---
type: "concept"
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources: ["a-philosophy-of-software-design"]
title: "Типові значення приховують рідкісні налаштування"
aliases: ["Defaults and overexposure"]
tags: ["source-note", "concept"]
created: "2026-09-21"
updated: "2026-09-21"
source: "chapter-5-excerpt"
---

# Типові значення приховують рідкісні налаштування

## Визначення

Розумні типові значення дозволяють користувачеві виконати звичайну задачу без знання всіх можливостей модуля. Окремий спосіб перевизначення залишає рідкісні налаштування доступними тим, кому вони потрібні: це часткове приховування інформації.

^aphsd-defaults-definition

## Чому це важливо

Вимога явно задавати значення, яке модуль уже може визначити, переносить його знання й роботу до клієнта. Overexposure виникає, коли звичайна можливість змушує вивчати рідкісні.

## Ознаки в коді

- Типове створення відповіді не вимагає вручну задавати всі службові поля.
- Рідкісні налаштування доступні окремими методами.
- Типова поведінка обирається з контексту, який модуль уже має.

## Межі та застосування

У прикладі розділу HTTP-бібліотека має обирати версію відповіді на основі запиту й задавати типовий Date. Це пояснення дизайну навчального API, а не повна специфікація HTTP.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-defaults|Розділ 5 — Defaults and overexposure]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-hiding-localizes-design-decisions|Приховування інформації локалізує проєктні рішення]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-leakage-couples-modules|Витік інформації зв’язує модулі спільним рішенням]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-temporal-decomposition-duplicates-knowledge|Часова декомпозиція дублює знання]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
