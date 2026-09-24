---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
  - "a-philosophy-of-software-design"
title: "Архітектура визначає вартість змін"
aliases:
  - "Architecture governs cost of change"
  - "Software should stay soft"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-07-26
source: "synthesis"
---

# Архітектура визначає вартість змін

## Визначення

Архітектура цінна не лише тим, що впорядковує систему, а тим, що утримує вартість змін у межах реального масштабу запиту. Якщо навіть невеликі зміни стають непропорційно дорогими через форму залежностей, модулів і рішень у коді, то архітектура вже працює проти продукту, а не на нього.

^architecture-cost-of-change-definition

## Чому це важливо

Ця ідея переводить архітектуру з площини смаку в площину економіки. Стейкхолдерам потрібна не абстрактно "красива" система, а така, у якій нові вимоги можна втілювати без постійного зростання часу, ризику й координаційних витрат. Саме тому гнучка структура є не другорядною технічною чеснотою, а передумовою довготривалої корисності ПЗ.

## Ознаки в коді

- Запити однакового масштабу вимагають дедалі більше торкань у різних частинах системи.
- Команда більше часу витрачає на страхування від побічних ефектів, ніж на саме впровадження зміни.
- Межі компонентів і залежності відбивають історію випадкових компромісів, а не логіку майбутньої еволюції системи.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-02-a-tale-of-two-values#^clean-architecture-ch02-thesis-softness]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-02-a-tale-of-two-values#^clean-architecture-ch02-thesis-scope-shape]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-02-a-tale-of-two-values#^clean-architecture-ch02-thesis-cost-growth]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-02-a-tale-of-two-values#^clean-architecture-ch02-quote-architecture-last]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-main-idea]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-thesis-investment-rate]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-rule-future-extension]]

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]
- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]

## Пов'язаний код

- Конкретні code notes для цього спільного концепту ще не додані.
