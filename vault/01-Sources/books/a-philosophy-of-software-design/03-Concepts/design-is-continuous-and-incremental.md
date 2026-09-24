---
type: concept
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
scope: "source-local"
sources:
  - "a-philosophy-of-software-design"
title: "Дизайн є безперервним та інкрементальним"
aliases:
  - "Software design is never done"
  - "Incremental development enables redesign"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-09-24
source: "chapter-1-and-3-excerpts"
---

# Дизайн є безперервним та інкрементальним

## Визначення

У програмних системах дизайн не закінчується після стартової фази проєкту. Оскільки систему можна суттєво змінювати вже під час розробки, хороший процес розтягує дизайн у часі: маленькі інкременти виявляють вади початкових рішень, а команда свідомо використовує це для постійного редизайну.

^aphsd-design-continuous-definition

## Чому це важливо

Цей концепт прямо протистоїть waterfall-мисленню, де дизайн вважається завершеним до реального зіткнення з кодом. Для ПЗ така модель небезпечна, бо проблеми архітектури зазвичай стають видимими лише тоді, коли система вже взаємодіє з реальними вимогами, залежностями й компромісами.

## Приклад

Команда спочатку зберігає поточну адресу email у таблиці `users`. Нова вимога — зберігати історію змін адреси. Тоді команда додає `user_email_history` і переносить туди відповідальність за історію, поки зміна схеми ще локальна. Додавати колонки `old_email`, `old_email_2` означало б закріпити випадкове обмеження й ускладнити наступні зміни. Дизайн уточнюється після появи реальної вимоги.

^aphsd-design-continuous-example

## Ознаки в коді

- Команда закладає час не лише на feature work, а й на покращення структури після нових спостережень.
- Архітектурні рішення можна коригувати без повного переписування системи.
- Кожна ітерація не тільки додає поведінку, а й очищує попередні неточності дизайну.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-continuous-design]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-waterfall]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-quote-incremental]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-thesis-continuous]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-rule-small-investments]]

## Пов'язані концепти

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]

## Пов'язаний код

- Окремі code notes для цього концепту ще не створені.
