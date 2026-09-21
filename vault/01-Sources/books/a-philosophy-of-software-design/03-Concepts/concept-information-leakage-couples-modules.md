---
type: "concept"
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources: ["a-philosophy-of-software-design"]
title: "Витік інформації зв’язує модулі спільним рішенням"
aliases: ["Information leakage"]
tags: ["source-note", "concept"]
created: "2026-09-21"
updated: "2026-09-21"
source: "chapter-5-excerpt"
---

# Витік інформації зв’язує модулі спільним рішенням

## Визначення

Витік інформації виникає, коли одне проєктне рішення закодоване в кількох модулях. Його зміна тоді потребує узгоджених змін у цих модулях, навіть якщо їхні публічні сигнатури не показують спільної залежності.

^aphsd-leakage-definition

## Чому це важливо

Два класи, які незалежно знають формат файла, залишаються зв’язаними цим форматом. Такий прихований витік важче помітити, ніж залежність, очевидну з API.

## Ознаки в коді

- Зміна формату змушує одночасно редагувати reader і writer.
- Клієнт знає, яку внутрішню колекцію повертає модуль і чому її не можна змінювати.
- Допоміжний клас лише передає всі деталі через getters, не створюючи абстракції.

## Межі та застосування

Невеликі тісно пов’язані класи можна об’єднати або винести спільне знання в окремий модуль. Другий варіант корисний лише тоді, коли його простий інтерфейс справді приховує рішення.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-leakage|Розділ 5 — Information leakage]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-hiding-localizes-design-decisions|Приховування інформації локалізує проєктні рішення]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-temporal-decomposition-duplicates-knowledge|Часова декомпозиція дублює знання]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-defaults-hide-uncommon-options|Типові значення приховують рідкісні налаштування]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
