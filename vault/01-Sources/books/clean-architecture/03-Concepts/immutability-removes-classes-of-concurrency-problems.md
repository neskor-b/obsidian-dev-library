---
type: concept
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
scope: "source-local"
sources:
  - "clean-architecture"
title: "Незмінність прибирає цілі класи проблем конкурентності"
aliases:
  - "Immutability removes classes of concurrency problems"
  - "Immutability as concurrency strategy"
tags:
  - source-note
  - concept
created: 2026-03-26
updated: 2026-04-18
source: "chapter-6-excerpt"
---

# Незмінність прибирає цілі класи проблем конкурентності

## Визначення

Архітектурна сила `immutability` у тому, що дані, які не змінюються після створення, не потребують координації на запис. Для таких даних не виникають `race condition`, `concurrent update problem` і значна частина deadlock-сценаріїв, бо немає самого акту спільного оновлення. У цій оптиці функціональне програмування важливе не як стиль запису, а як спосіб прибрати проблему на рівні моделі стану.

^clean-architecture-immutability-concurrency-definition

## Чому це важливо

Цей концепт змінює архітектурне питання з "як краще синхронізувати все mutable" на "скільки mutable взагалі лишити в системі". Що менше спільного змінного стану, то менше система залежить від блокувань, складної координації потоків і крихких домовленостей щодо порядку запису. Виграш тут не лише в безпечності, а й у простоті міркування: `immutable` потік даних легше тестувати, розпаралелювати й переносити між компонентами.

## Ознаки в коді

- Основна бізнес-логіка виражена як перетворення значень, а не як послідовність мутацій спільних об'єктів.
- Потоки або процеси обмінюються повідомленнями, значеннями чи подіями, а не спільними mutable-структурами.
- Стан або взагалі не оновлюється на місці, або його зміна відтиснута в дуже вузькі межі застосунку.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-03-paradigm-overview#^clean-architecture-ch03-thesis-functional]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-06-functional-programming#^clean-architecture-ch06-main-idea]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-06-functional-programming#^clean-architecture-ch06-thesis-no-mutation]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-06-functional-programming#^clean-architecture-ch06-thesis-concurrency]]

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/03-Concepts/paradigms-impose-discipline|Парадигми вводять дисципліну через обмеження]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-06-functional-programming|Розділ 6. Функціональне програмування]]

## Пов'язаний фрагмент

- [[01-Sources/books/clean-architecture/02-Chapters/ch-06-functional-programming#^clean-architecture-ch06-code-atom|Clojure atom дисциплінує мутацію через swap!]]
