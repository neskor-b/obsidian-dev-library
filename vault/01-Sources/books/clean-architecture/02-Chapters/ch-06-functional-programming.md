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
updated: 2026-09-24
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

- У функціональному стилі значення після ініціалізації не змінюються: variables do not vary. ^clean-architecture-ch06-thesis-no-mutation
- Незмінний стан усуває частину гонок під час конкурентного доступу та зменшує потребу в блокуваннях. ^clean-architecture-ch06-thesis-concurrency
- Практичний компроміс — segregation of mutability: більша частина системи працює з незмінними значеннями, а зміни стану ізолюються й захищаються. ^clean-architecture-ch06-thesis-segregation
- `Clojure atom` і `swap!` показують контрольовану локальну зміну: функція обчислює нове значення, а атом оновлюється через повторювану операцію порівняння та заміни. ^clean-architecture-ch06-thesis-atom
- `Event sourcing` зберігає послідовність подій; поточний стан можна відновити їх застосуванням або зі знімка. ^clean-architecture-ch06-thesis-event-sourcing

Абсолютна незмінність може бути дорогою за пам'яттю чи часом, тому межі мутації варто проєктувати свідомо. ^clean-architecture-ch06-thesis-pragmatic-limits

Append-only журнал зменшує потребу в оновленні минулих записів, але поточний стан і правила його зміни все одно потребують узгодження. ^clean-architecture-ch06-thesis-cr-not-crud

## Приклад коду

### Clojure atom дисциплінує мутацію через `swap!`

```clojure showLineNumbers
(def counter (atom 0)) ; initialize counter to 0
(swap! counter inc)    ; safely increment counter.
```

^clean-architecture-ch06-code-atom

Цей фрагмент показує, як функціональна система може дозволяти мутацію лише в дуже дисциплінованій формі. `atom` огортає змінний стан, а `swap!` не записує значення напряму, а приймає функцію, яка обчислює новий стан з поточного. Під капотом це реалізується через `compare-and-swap`: якщо хтось змінив значення паралельно, операція повторюється. Так мутація лишається локальною, явною й захищеною.

Такий механізм добре працює для простих незалежних значень, але не гарантує коректну координацію кількох взаємозалежних змінних. Якщо бізнес-інваріанти розкидані між кількома mutable-осередками, одного `atom` або `swap!` може бути замало, і знадобиться сильніша транзакційна модель.

### Банківський рахунок як append-only журнал

Замість безпосередньої зміни поля `balance` можна записувати підтверджені операції:

```sql
INSERT INTO transactions (account_id, amount, type)
VALUES (42, -100, 'withdrawal');
```

Поточний баланс обчислюється з початкової суми та послідовності операцій рахунка. Два конкурентні `INSERT` можуть зберегти обидві події, але сам журнал не гарантує, що списання дозволені: перевірку достатності коштів треба виконувати атомарно щодо інших списань, наприклад серіалізувати команди одного рахунка або застосувати транзакційне блокування. Так само `UPDATE accounts SET balance = balance - 100` у належній транзакції не є сам собою «втраченою зміною». Журнал допомагає відтворювати історію; інваріант балансу забезпечує окремий механізм.

^clean-architecture-ch06-example-bank-ledger

## Важливі цитати

> Variables in functional languages do not vary.

^clean-architecture-ch06-quote-variables

> Architects would be wise to push as much processing as possible into the immutable components.

^clean-architecture-ch06-quote-architects

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-03-paradigm-overview|Розділ 3. Огляд парадигм]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming|Попередній розділ: Об'єктно-орієнтоване програмування]]

