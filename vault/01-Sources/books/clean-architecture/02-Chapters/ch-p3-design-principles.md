---
type: chapter
source_type: books
source_slug: clean-architecture
source_title: Clean Architecture
chapter: Part III
title: Принципи дизайну (SOLID)
aliases:
  - Design Principles
  - SOLID overview
tags:
  - source-note
  - chapter
created: 2026-04-14
updated: 2026-09-24
source: excerpt
---

# Принципи дизайну (SOLID)

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Частина книги: III
- Тип джерела: уривок

## Головна ідея

Між clean code і high-level architecture лежить проміжний рівень дизайну: модулі, класи й інші групування функцій та даних. Якість окремих "цеглин" ще не гарантує доброї системи. Принципи дизайну допомагають складати ці елементи в структури, що витримують зміни, залишаються зрозумілими та стають основою для повторно використовуваних компонентів.

^clean-architecture-p3-main-idea

## Ключові тези

- `SOLID` стосується не лише класичного `object-oriented` коду: будь-яка система має групування функцій і даних, а отже має і проблему того, як ці групування пов'язувати між собою. ^clean-architecture-p3-thesis-groupings
- Мета принципів полягає у створенні `mid-level software structures`, які толерують зміни, легко читаються й стають хорошою основою для компонентів. ^clean-architecture-p3-thesis-mid-level
- `Mid-level` означає рівень між окремими рядками коду та високорівневою архітектурою: саме тут програміст вирішує, які модулі існують, за що вони відповідають і як залежать один від одного. ^clean-architecture-p3-thesis-module-level
- Добре спроєктовані модулі самі по собі ще не гарантують гарної системи, тому після `SOLID` розмова природно переходить до принципів компонентів і далі до high-level architecture. ^clean-architecture-p3-thesis-ladder
- Огляд `SOLID` у цьому уривку формулює п'ять окремих напрямів дисципліни: одна причина для зміни (`SRP`), розширення через додавання коду (`OCP`), взаємозамінність частин через контракт (`LSP`), залежність лише від потрібних інтерфейсів (`ISP`) і підпорядкування деталей політикам (`DIP`). ^clean-architecture-p3-thesis-five-principles
- Історично набір принципів складався поступово від дискусій наприкінці 1980-х до стабілізації на початку 2000-х, а акронім `SOLID` закріпився після пропозиції Майкла Фезерса. ^clean-architecture-p3-thesis-history

## Приклад: одна причина розширення функціоналу

Уяви клас `OrderProcessor`, який одночасно рахує знижки, друкує чек і зберігає замовлення в базі. Кожна з цих трьох задач — окрема причина для зміни: маркетинг змінює правила знижок, бухгалтерія — формат чека, DBA — схему таблиці. `SOLID` як маршрут перевірки означає: перш ніж додавати четверту причину для зміни (наприклад, надсилання email), спершу запитати, чи цей клас уже несе забагато відповідальностей. Наступні п'ять розділів деталізують кожен з п'яти принципів на цьому маршруті.

^clean-architecture-p3-example-order-processor

## Важливі цитати

> The SOLID principles apply to those groupings.

^clean-architecture-p3-quote-groupings

> Details should depend on policies.

^clean-architecture-p3-quote-dip

## Пов'язані концепти

- [[03-Maps/solid-and-clean-architecture-principles|SOLID організовує модулі для змінюваності]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[02-Concepts/dependency-inversion|Інверсія залежностей]]

## Пов'язані приклади коду

- Конкретні code notes для цього вступного уривка ще не додані.

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- Наступні розділи цієї частини деталізують [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle|SRP]], [[01-Sources/books/clean-architecture/02-Chapters/ch-08-open-closed-principle|OCP]], [[01-Sources/books/clean-architecture/02-Chapters/ch-09-liskov-substitution-principle|LSP]], [[01-Sources/books/clean-architecture/02-Chapters/ch-10-interface-segregation-principle|ISP]] і [[01-Sources/books/clean-architecture/02-Chapters/ch-11-dependency-inversion-principle|DIP]]; спільний міжджерельний сенс `DIP` у цьому vault винесено окремо в [[02-Concepts/dependency-inversion|концепт про інверсію залежностей]].
