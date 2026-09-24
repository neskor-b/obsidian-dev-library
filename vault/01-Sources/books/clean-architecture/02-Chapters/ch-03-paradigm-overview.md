---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "3"
title: "Огляд парадигм"
aliases:
  - "Paradigm Overview"
tags:
  - source-note
  - chapter
created: 2026-03-24
updated: 2026-03-25
source: "excerpt"
---

# Огляд парадигм

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 3
- Тип джерела: уривок

## Головна ідея

Роберт Мартін розглядає три ключові парадигми програмування як три різні форми дисципліни, які не розширюють можливості розробника, а навпаки обмежують певні дії. Саме через ці обмеження парадигми стають корисними для архітектури: структурне програмування дисциплінує алгоритмічний контроль, об'єктно-орієнтоване програмування дисциплінує перетин меж через поліморфізм, а функціональне програмування дисциплінує роботу з даними через обмеження змінності.

^clean-architecture-ch03-main-idea

## Ключові тези

- `Structured programming` накладає дисципліну на пряме передавання керування, замінюючи нестримані переходи на керовані конструкції на кшталт `if/then/else` і `do/while/until`. ^clean-architecture-ch03-thesis-structured
- `Object-oriented programming` накладає дисципліну на непряме передавання керування; у цьому розділі Мартін пов'язує це насамперед із поліморфізмом та перетином архітектурних меж. ^clean-architecture-ch03-thesis-oop
- `Functional programming` накладає дисципліну на присвоєння, а центральною ідеєю тут є обмеження змінності даних через immutability. ^clean-architecture-ch03-thesis-functional
- Усі три парадигми є "негативними" за наміром: вони радше забороняють певні дії, ніж додають нові виражальні засоби. ^clean-architecture-ch03-thesis-negative
- Саме тому парадигми напряму стосуються архітектури: вони дають основу для алгоритмів, відокремлення компонентів і керування даними. ^clean-architecture-ch03-thesis-architecture

## Важливі цитати

> Each of the paradigms removes capabilities from the programmer.

^clean-architecture-ch03-quote-removes

> Structured programming imposes discipline on direct transfer of control.

^clean-architecture-ch03-quote-structured

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]

## Пов'язані приклади коду

- Окремі code notes для цього розділу ще не створені.

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]

