---
type: concept
scope: source-local
source_type: books
source_slug: a-philosophy-of-software-design
source_title: A Philosophy of Software Design
sources: [a-philosophy-of-software-design]
title: "Помірно універсальний інтерфейс"
aliases: ["Somewhat general-purpose interfaces"]
tags: [source-note, concept]
created: 2026-09-22
updated: 2026-09-22
source: chapter-6-excerpt
---

# Помірно універсальний інтерфейс

## Визначення

**Помірно універсальний інтерфейс дає прості операції для кількох сценаріїв, тоді як реалізовані можливості відповідають поточним потребам.** Модуль не повторює всі дії конкретного клієнта у своїх методах, але залишається зручним для нього.

^aphsd-somewhat-general-definition

## Чому це важливо

Клієнту потрібно вивчити менше операцій, а модулю — знати менше про клієнта. Користь з’являється вже у поточному коді; майбутнє повторне використання є додатковою перевагою.

## Приклад із книги

Текстовий клас надає `delete(start, end)`. Інтерфейс редактора визначає діапазон для Backspace, Delete чи виділення. Правила клавіш залишаються в редакторі, а механізм зміни тексту — у текстовому класі.

## Ознаки в коді

- Одна зрозуміла операція підтримує кілька поточних сценаріїв.
- Назви й типи описують предмет роботи модуля, а не конкретний екран чи кнопку.
- Звичайна задача виконується кількома простими викликами.
- Зменшення кількості методів не породжує безлічі режимів і параметрів.

## Межа узагальнення

Якщо API вміє видаляти лише один символ, клієнтам потрібні цикли для видалення діапазонів. Формальна простота інтерфейсу перекладає роботу назовні. Універсальність має поєднуватися зі зручними операціями потрібного масштабу.

Не потрібно додавати функціональність лише тому, що вона може знадобитися колись. Потрібно знайти спільні операції для вже відомих потреб.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-06-general-purpose-modules-are-deeper#^aphsd-ch06-generality|Розділ 6. Баланс універсальності]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-06-general-purpose-modules-are-deeper#^aphsd-ch06-questions|Три запитання для перевірки API]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-06-general-purpose-modules-are-deeper#^aphsd-ch06-ranges|Чому потрібні операції над діапазонами]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-hiding-localizes-design-decisions|Приховування інформації локалізує проєктні рішення]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/abstractions-must-preserve-important-details|Абстракції мають зберігати важливі деталі]]
