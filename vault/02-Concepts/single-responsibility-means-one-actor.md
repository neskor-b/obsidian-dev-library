---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
title: "SRP означає одного актора, а не одну дію"
aliases:
  - "Single responsibility means one actor"
  - "A module should be responsible to one actor"
tags:
  - source-note
  - concept
created: 2026-04-14
updated: 2026-04-18
source: "synthesis"
---

# SRP означає одного актора, а не одну дію

## Визначення

`Single Responsibility Principle` не вимагає, щоб модуль виконував лише одну дрібну операцію. Його реальний зміст у тому, що модуль має бути відповідальним перед одним актором, тобто перед однією узгодженою причиною для зміни. Якщо в одному модулі змішані потреби кількох акторів, то cohesion стає фальшивою: модуль виглядає цілісним лише технічно, але не організаційно.

^single-responsibility-means-one-actor-definition

## Чому це важливо

Цей концепт допомагає проводити межі модулів не за назвами сутностей, а за тиском змін. Саме тому `SRP` зменшує не лише складність читання, а й організаційний ризик: зміни для одного актора перестають випадково ламати сценарії іншого, а окремі команди рідше стикаються в одному файлі через несумісні правки.

## Ознаки в коді

- Один модуль містить поведінку для різних бізнес-функцій або різних команд, хоча всі вони крутяться навколо однієї сутності на кшталт `Employee` чи `Order`.
- "Спільні" helper-функції використовуються в кількох сценаріях з різним бізнесовим сенсом, і зміна для одного сценарію ризикує пошкодити інший.
- Один і той самий файл регулярно стає місцем merge-конфліктів між розробниками, які реалізують незалежні запити на зміни.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-main-idea]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-thesis-one-actor]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-thesis-accidental-duplication]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-thesis-merges]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-quote-actor]]

## Пов'язані концепти

- [[03-Maps/solid-and-clean-architecture-principles|SOLID організовує модулі для змінюваності]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]

## Пов'язаний фрагмент

- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle#^clean-architecture-ch07-code-employee-split|SRP розділяє Employee за акторами]]
