---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "Part IV"
title: "Принципи компонентів"
aliases:
  - "Component Principles"
  - "Part IV"
tags:
  - source-note
  - chapter
created: 2026-04-21
updated: 2026-04-21
source: "excerpt"
---

# Принципи компонентів

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Частина книги: IV
- Тип джерела: уривок

## Головна ідея

Цей вступ піднімає масштаб розмови на щабель вище за `SOLID`. Якщо принципи дизайну пояснювали, як складати "цеглини" у стіни й кімнати, то принципи компонентів пояснюють, як складати самі кімнати в цілісну будівлю. Мартін переводить фокус із модулів і класів на компоненти як більші одиниці побудови системи, а далі обіцяє розібрати, з чого вони складаються і як мають поєднуватися в архітектуру.

^clean-architecture-p4-main-idea

## Ключові тези

- Після `SOLID` природним наступним рівнем стає не одразу "велика архітектура", а компоненти: більші структурні одиниці, з яких збирають великі системи. ^clean-architecture-p4-thesis-next-level
- Мета цієї частини - відповісти на три питання: що таке software components, які елементи входять до їхнього складу і як ці компоненти мають комбінуватися в системи. ^clean-architecture-p4-thesis-three-questions
- Аналогія з будівлею важлива не як метафора краси, а як підказка масштабу: модулі й класи вже не є кінцевою структурною одиницею архітектурного мислення. ^clean-architecture-p4-thesis-scale
- Компонентні принципи продовжують лінію від clean code через design principles до system architecture, тобто з'єднують локальні рішення про код із рішеннями про розгортання, межі й еволюцію системи. ^clean-architecture-p4-thesis-bridge

## Важлива цитата

> the component principles tell us how to arrange the rooms into buildings.

^clean-architecture-p4-quote-rooms-buildings

## Пов'язані концепти

- [[02-Concepts/solid-organizes-modules-for-change|SOLID організовує модулі для змінюваності]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles|Попередня частина: Принципи дизайну]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-12-components|Наступний розділ: Компоненти]]
