---
type: concept
scope: "shared-evergreen"
sources:
  - "a-philosophy-of-software-design"
title: "Складність є центральною проблемою дизайну ПЗ"
aliases:
  - "Complexity is the central design problem"
  - "Software design is about complexity"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-07-26
source: "synthesis"
---

# Складність є центральною проблемою дизайну ПЗ

## Визначення

У довгоживучому програмному забезпеченні головний ворог не обсяг коду сам по собі, а складність, яка заважає людям розуміти систему під час змін. Тому дизайн варто оцінювати не лише за коректністю чи функціональністю, а за тим, наскільки він стримує зростання когнітивного навантаження і не змушує кожну зміну торкатися надто великої частини системи.

^complexity-central-design-problem-definition

## Чому це важливо

Цей концепт дає спільну мову для рішень різного масштабу: від найменувань і special cases до модульних меж і процесу розробки. Коли складність стає основним критерієм, дизайн перестає бути питанням смаку й перетворюється на практику зменшення ризику, вартості змін і темпу деградації системи.

## Ознаки в коді

- Проста на вигляд зміна вимагає врахування багатьох прихованих залежностей або неочевидних правил.
- Щоб бути впевненим у зміні, розробник мусить одночасно утримувати в голові забагато деталей системи.
- Для розуміння локальної поведінки доводиться читати занадто багато стороннього коду, документації чи історичних домовленостей.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-main-idea]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-understanding]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-accumulates]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-quote-complexity]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-main-idea]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-thesis-experience]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-thesis-causes]]

## Пов'язані концепти

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/red-flags-guide-design-judgment|Red flags спрямовують дизайнерське судження]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/complexity-accumulates-incrementally|Складність накопичується інкрементально]]

## Пов'язаний код

- Конкретні code notes для цього спільного концепту ще не додані.
