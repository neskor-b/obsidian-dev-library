---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "4"
title: "Структурне програмування"
aliases:
  - "Structured Programming"
tags:
  - source-note
  - chapter
created: 2026-03-24
updated: 2026-09-24
source: "excerpt"
---

# Структурне програмування

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 4
- Тип джерела: уривок

## Головна ідея

Цінність `structured programming` не зводиться до стилю запису `if` і `while`. Його головна сила в тому, що воно обмежує хаотичне передавання керування, дозволяє рекурсивно декомпозувати поведінку на малі одиниці та робить програму придатною до перевірки. У сучасній практиці ця перевірка відбувається не через формальні математичні докази, а через фальсифікацію: ми намагаємося тестами довести код неправильним і вважаємо його достатньо коректним, якщо це не вдається.

^clean-architecture-ch04-main-idea

## Ключові тези

- `Edsger Dijkstra` шукав для програмування дисципліну рівня науки: у крихкому світі ранніх комп'ютерів помилка в одній деталі легко руйнувала всю програму, тому він звернувся до ідеї доказу коректності. ^clean-architecture-ch04-thesis-dijkstra
- Нестримане `goto` заважає рекурсивно розкладати модулі на менші одиниці; натомість послідовність, вибір і ітерація зберігають структуру, придатну до міркування та локальної перевірки. ^clean-architecture-ch04-thesis-control-structures
- Саме тому `structured programming` стало основою функціональної декомпозиції: великі задачі можна послідовно розбивати на високорівневі й далі дедалі дрібніші функції. ^clean-architecture-ch04-thesis-functional-decomposition
- Формальні евклідові докази так і не стали повсякденною практикою розробки; у підсумку програмування виявилося ближчим до науки, ніж до чистої математики. ^clean-architecture-ch04-thesis-science-not-math
- Тести не доводять відсутність помилок, а лише можуть виявити їхню присутність, тому цінність тестування полягає у спробі спростувати коректність, а не остаточно її засвідчити. ^clean-architecture-ch04-thesis-tests-falsify
- На архітектурному рівні ця логіка не зникає: хороші модулі, компоненти й сервіси мають бути легко фальсифікованими, тобто ізольованими та тестовними. ^clean-architecture-ch04-thesis-architecture

## Приклад: тест як спроба спростувати

```java
@Test
void excessiveDiscountIsRejectedWithoutChangingTotal() {
    Order order = new Order(5.00);
    assertThrows(IllegalArgumentException.class,
        () -> order.applyDiscount(200)); // навмисно недопустимий відсоток
    assertEquals(5.00, order.getTotal());
}
```

У цьому прикладі контракт `applyDiscount` вимагає відхиляти відсоток понад 100 винятком і залишати суму незмінною. Тест навмисно шукає порушення цього контракту. Якщо одне з очікувань падає, спроба фальсифікації вдалася й виявила дефект. Якщо тест зелений, спроба не знайшла дефекту в цьому сценарії; вона не доводить коректність для всіх входів.

^clean-architecture-ch04-example-falsifying-test

## Важливі цитати

> Go To Statement Considered Harmful.

^clean-architecture-ch04-quote-goto

> Testing shows the presence, not the absence, of bugs.

^clean-architecture-ch04-quote-testing

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-03-paradigm-overview|Розділ 3. Огляд парадигм]]
- [[02-Concepts/tests-falsify-not-prove-correctness|Тести спростовують помилки, а не доводять коректність]]

## Пов'язані приклади коду

- Окремі code notes для цього розділу ще не створені.

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-03-paradigm-overview|Попередній розділ: Огляд парадигм]]

## Пов'язані нотатки

- [[02-Concepts/tests-falsify-not-prove-correctness#^tests-falsify-not-prove-correctness-definition|Спільний концепт про тести й фальсифікацію]]
