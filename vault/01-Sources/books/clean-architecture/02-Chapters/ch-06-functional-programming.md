---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "6"
title: "Функціональне програмування"
aliases:
  - "Functional Programming"
tags:
  - source-note
  - chapter
created: 2026-03-26
updated: 2026-04-18
source: "excerpt"
---

# Функціональне програмування

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 6
- Тип джерела: уривок

## Головна ідея

У цьому розділі Роберт Мартін показує архітектурний сенс `functional programming` не через синтаксис `Lisp` чи `Clojure`, а через дисципліну незмінності. Якщо дані не змінюються після створення, то зникають цілі класи проблем конкурентності, а отже архітектура може спиратися на простіші й надійніші моделі виконання. Практичний висновок для архітектора такий: треба виштовхувати якомога більше логіки в `immutable` частини системи, а неминучу мутацію ізолювати, захищати й робити максимально вузькою.

^clean-architecture-ch06-main-idea

## Ключові тези

- У функціональному стилі змінні ініціалізуються, але не модифікуються; саме тому Мартін формулює тезу, що в функціональних мовах variables do not vary. ^clean-architecture-ch06-thesis-no-mutation
- Архітектурна цінність `immutability` у тому, що race conditions, concurrent update problems і lock-based deadlocks походять від змінного стану та механізмів його захисту. ^clean-architecture-ch06-thesis-concurrency
- Абсолютна незмінність була б найлегшою моделлю, але в реальних системах її стримують обмеження пам'яті та продуктивності, тому потрібні практичні компроміси. ^clean-architecture-ch06-thesis-pragmatic-limits
- Найтиповіший компроміс полягає в segregation of mutability: велика частина системи лишається функціональною, а вузькі ділянки зміни стану захищаються транзакційною пам'яттю, `compare-and-swap` або схожими дисциплінами. ^clean-architecture-ch06-thesis-segregation
- `Clojure atom` і `swap!` демонструють контрольовану локальну мутацію: нове значення обчислюється функцією, а запис відбувається лише якщо порівняння з поточним станом успішне; інакше операція повторюється. ^clean-architecture-ch06-thesis-atom
- `Event sourcing` зсуває систему ще далі в бік незмінності: ми зберігаємо не поточний стан, а історію транзакцій або подій, а стан за потреби відновлюємо через replay чи snapshot. ^clean-architecture-ch06-thesis-event-sourcing
- Якщо сховище є append-only, а `update` і `delete` не виконуються, то система перестає бути класичною `CRUD`-моделлю й уникає частини проблем конкурентного оновлення на рівні даних. ^clean-architecture-ch06-thesis-cr-not-crud

## Приклад коду

### Clojure atom дисциплінує мутацію через `swap!`

```clojure showLineNumbers
(def counter (atom 0)) ; initialize counter to 0
(swap! counter inc)    ; safely increment counter.
```

^clean-architecture-ch06-code-atom

Цей фрагмент показує, як функціональна система може дозволяти мутацію лише в дуже дисциплінованій формі. `atom` огортає змінний стан, а `swap!` не записує значення напряму, а приймає функцію, яка обчислює новий стан з поточного. Під капотом це реалізується через `compare-and-swap`: якщо хтось змінив значення паралельно, операція повторюється. Так мутація лишається локальною, явною й захищеною.

Такий механізм добре працює для простих незалежних значень, але не гарантує коректну координацію кількох взаємозалежних змінних. Якщо бізнес-інваріанти розкидані між кількома mutable-осередками, одного `atom` або `swap!` може бути замало, і знадобиться сильніша транзакційна модель.

## Важливі цитати

> Variables in functional languages do not vary.

^clean-architecture-ch06-quote-variables

> Architects would be wise to push as much processing as possible into the immutable components.

^clean-architecture-ch06-quote-architects

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/03-Concepts/immutability-removes-classes-of-concurrency-problems|Незмінність прибирає цілі класи проблем конкурентності]]
- [[01-Sources/books/clean-architecture/03-Concepts/paradigms-impose-discipline|Парадигми вводять дисципліну через обмеження]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming|Попередній розділ: Об'єктно-орієнтоване програмування]]

## Пов'язані нотатки

- [[01-Sources/books/clean-architecture/03-Concepts/immutability-removes-classes-of-concurrency-problems#^clean-architecture-immutability-concurrency-definition|Локальний концепт про незмінність і concurrency]]
