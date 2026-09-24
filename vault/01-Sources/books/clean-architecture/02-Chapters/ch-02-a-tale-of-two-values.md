---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "2"
title: "Історія про дві цінності"
aliases:
  - "A Tale of Two Values"
tags:
  - source-note
  - chapter
created: 2026-03-24
updated: 2026-03-25
source: "excerpt"
---

# Історія про дві цінності

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 2
- Тип джерела: уривок

## Головна ідея

Програмне забезпечення має дві цінності для стейкхолдерів: поточну поведінку системи й її здатність дешево змінюватися. Перша цінність зазвичай відчувається як термінова, але друга є стратегічно важливішою, бо саме структура системи визначає, чи зможе команда й надалі втілювати нові вимоги без вибухового росту вартості змін.

^clean-architecture-ch02-main-idea

## Ключові тези

- Поведінка системи є лише першою цінністю програмного забезпечення: розробники справді мають реалізовувати вимоги й виправляти дефекти, але цим їхня роль не вичерпується. ^clean-architecture-ch02-thesis-behavior
- Друга цінність полягає в "м'якості" software: систему має бути легко змінювати, коли змінюються потреби стейкхолдерів. ^clean-architecture-ch02-thesis-softness
- Складність змін має визначатися масштабом запиту, а не випадковою формою поточної архітектури. ^clean-architecture-ch02-thesis-scope-shape
- Коли архітектура підлаштована лише під вчорашню форму задач, кожен наступний запит стає дорожчим, навіть якщо його реальний обсяг не зростає. ^clean-architecture-ch02-thesis-cost-growth
- Система, яка зараз працює, але практично не піддається змінам, з часом стає марною; система, яку легко змінювати, можна зробити коректною й утримувати коректною надалі. ^clean-architecture-ch02-thesis-greater-value
- Поведінка часто виглядає терміновою, тоді як архітектура є важливою, але не терміновою; саме тому команда має свідомо захищати архітектуру від витіснення короткостроковими фічами. ^clean-architecture-ch02-thesis-eisenhower
- Матриця Айзенхауера допомагає відрізняти справді важливе від просто термінового: не все, що тисне по часу, однаково цінне для довгострокової корисності системи. ^clean-architecture-ch02-thesis-matrix-priorities
- У запропонованому порядку пріоритетів архітектура опиняється в перших двох позиціях, бо належить до важливого, тоді як поведінка може бути або водночас важливою й терміновою, або лише терміновою. ^clean-architecture-ch02-thesis-architecture-top-two
- Відстоювати архітектуру є прямою відповідальністю команди розробки й особливо архітектора, бо бізнес не може самостійно адекватно оцінити її важливість. ^clean-architecture-ch02-thesis-fight

## Важливі цитати

> The urgent are not important, and the important are never urgent.

^clean-architecture-ch02-quote-eisenhower

> Software was invented to be "soft."

^clean-architecture-ch02-quote-soft

> If architecture comes last, then the system will become ever more costly to develop, and eventually change will become practically impossible for part or all of the system.

^clean-architecture-ch02-quote-architecture-last

## Пов'язані концепти

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]

## Пов'язані приклади коду

- Окремі code notes для цього розділу ще не створені.

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]

## Пов'язані нотатки

- [[02-Concepts/architecture-governs-cost-of-change#^architecture-cost-of-change-definition|Визначення архітектури як чинника вартості змін]]
