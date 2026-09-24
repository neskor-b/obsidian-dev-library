---
type: concept
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
scope: "source-local"
sources:
  - "clean-architecture"
title: "Єдність дизайну й архітектури"
aliases:
  - "Design and architecture continuum"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-03-25
source: "chapter-1-excerpt"
---

# Єдність дизайну й архітектури

## Визначення

У межах цієї книги архітектура і дизайн розглядаються як одна безперервна послідовність рішень. Високорівнева форма системи, межі компонентів, залежності й дрібні реалізаційні деталі не можна чесно розділити на "архітектуру" і "просто код", бо всі вони разом визначають, наскільки система придатна до змін.

^clean-architecture-design-continuum-definition

## Чому це важливо

Цей концепт прибирає небезпечну ілюзію, що архітектурою можна займатися окремо від щоденного коду. Якщо архітектурні рішення не доходять до рівня модулів, тестів, залежностей і локальних угод у коді, то вони не керують системою, а лише прикрашають документацію.

## Ознаки в коді

- Високорівневі межі системи видно в залежностях і структурі модулів, а не лише на діаграмах.
- Деталі реалізації не суперечать основним архітектурним намірам.
- Рішення про тести, інтерфейси, назви та ізоляцію компонентів підтримують загальну форму системи.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture#^clean-architecture-ch01-main-idea]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture#^clean-architecture-ch01-thesis-house]]

## Пов'язані концепти

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]

## Пов'язаний код

- Окремі code notes для цього концепту ще не створені.
