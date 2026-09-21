---
type: "concept"
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources: ["a-philosophy-of-software-design"]
title: "Часова декомпозиція дублює знання"
aliases: ["Temporal decomposition"]
tags: ["source-note", "concept"]
created: "2026-09-21"
updated: "2026-09-21"
source: "chapter-5-excerpt"
---

# Часова декомпозиція дублює знання

## Визначення

Часова декомпозиція розділяє модулі за порядком виконання операцій. Вона спричиняє витік, коли різні етапи потребують того самого знання, наприклад формату файла під час читання й запису.

^aphsd-temporal-definition

## Чому це важливо

Послідовність операцій потрібна для керування виконанням, але сама по собі не визначає хороших меж модулів. Формат доцільно зосередити в одному модулі, який викликають на різних етапах.

## Ознаки в коді

- Класи відповідають етапам «спочатку прочитати, потім розібрати», але обидва розбирають заголовки.
- Клієнт мусить викликати кілька поверхневих API в заданому порядку.
- Одне правило повторюється на різних етапах обробки.

## Межі та застосування

Поділ за етапами допустимий, якщо етапи використовують різні знання й межі підтримують приховування інформації. Сам порядок виконання не є доказом поганого дизайну.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-temporal|Розділ 5 — Temporal decomposition]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-hiding-localizes-design-decisions|Приховування інформації локалізує проєктні рішення]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-leakage-couples-modules|Витік інформації зв’язує модулі спільним рішенням]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-defaults-hide-uncommon-options|Типові значення приховують рідкісні налаштування]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
