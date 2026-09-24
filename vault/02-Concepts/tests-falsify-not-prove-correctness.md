---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
title: "Тести спростовують помилки, а не доводять коректність"
aliases:
  - "Tests falsify, not prove correctness"
  - "Testing shows presence, not absence of bugs"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-09-24
source: "synthesis"
---

# Тести спростовують помилки, а не доводять коректність

## Визначення

Тестування в програмуванні ближче до наукової фальсифікації, ніж до математичного доказу. Ми не можемо остаточно довести, що система правильна за всіх можливих умов, але можемо цілеспрямовано шукати сценарії, які зроблять її явно неправильною. Якщо такі спроби не спрацьовують, код стає не "доведеним", а достатньо надійним для практичного використання.

^tests-falsify-not-prove-correctness-definition

## Чому це важливо

Цей концепт допомагає будувати чеснішу інженерну культуру. Він знімає небезпечну ілюзію, що наявність тестів гарантує безпомилковість, і водночас підкреслює справжню мету тестування: створювати умови, у яких система може бути спростована. Звідси природно випливає і вимога до дизайну: модулі мають бути малими, ізольованими й спостережуваними.

## Приклад

```java
@Test
void excessiveWithdrawalCannotOverdrawAccount() {
    Account account = new Account(100);
    assertThrows(InsufficientFundsException.class,
        () -> account.withdraw(1_000_000)); // навмисно екстремальний вхід
    assertEquals(100, account.getBalance());
}
```

У цьому прикладі контракт `withdraw` вимагає відхиляти надмірне списання винятком і зберігати початковий баланс. Тест навмисно шукає контрприклад. Якщо очікування падає, спроба фальсифікації вдалася й виявила дефект. Якщо тест зелений, спроба не знайшла дефекту в цьому сценарії. Паралельні списання або інші стани рахунка потребують окремих перевірок; зелений тест не засвідчує коректність для них.

^tests-falsify-example

## Ознаки в коді

- Тести сформульовані як спроби зламати припущення про поведінку, а не як ритуальне покриття рядків.
- Компоненти мають чіткі входи, виходи та межі, щоб помилку можна було локалізувати.
- Команда трактує "зелений" набір тестів як тимчасову робочу впевненість, а не як абсолютний доказ.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming#^clean-architecture-ch04-thesis-science-not-math]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming#^clean-architecture-ch04-thesis-tests-falsify]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming#^clean-architecture-ch04-thesis-architecture]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming#^clean-architecture-ch04-quote-testing]]

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming|Розділ 4. Структурне програмування]]

## Пов'язаний код

- Конкретні code notes для цього спільного концепту ще не додані.
