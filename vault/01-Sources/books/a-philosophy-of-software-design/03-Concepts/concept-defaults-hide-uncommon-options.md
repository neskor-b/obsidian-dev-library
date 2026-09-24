---
type: "concept"
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources: ["a-philosophy-of-software-design"]
title: "Типові значення приховують рідкісні налаштування"
aliases: ["Defaults and overexposure"]
tags: ["source-note", "concept"]
created: "2026-09-21"
updated: "2026-09-24"
source: "chapter-5-and-8-excerpts"
---

# Типові значення приховують рідкісні налаштування

## Визначення

**Типове значення — це значення, яке модуль використовує, якщо його не задали явно.** Добре обрані типові значення дозволяють виконати звичайну задачу без довгого списку налаштувань. Особливі налаштування залишаються доступними за потреби.

^aphsd-defaults-definition

Приклад із розділу 5: HTTP-бібліотека сама визначає версію відповіді й дату замість того, щоб змушувати кожного викликача задавати їх вручну — [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-defaults|детальніше в розділі 5]].

## Чому це важливо

Людина вивчає лише те, що потрібне для її задачі. Їй не доводиться налаштовувати можливості, якими вона не користується.

Коли простий виклик вимагає розібратися з усіма рідкісними опціями, виникає *overexposure* — надмірне розкриття можливостей.

## Автоматичний вибір замість обов’язкового налаштування

Типове значення може бути не лише статичним, а й обчисленим: модуль сам вимірює умови (наприклад, швидкість відповідей) і на основі цього обирає значення — це стійкіше за ручне налаштування, яке може застаріти ([[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-08-pull-complexity-downwards#^aphsd-ch08-configuration|розділ 8]]). Явний параметр лишається доречним, коли рішення залежить від знань, недоступних модулю.

^aphsd-defaults-adaptive

## Власний приклад

```typescript
function connect(host: string, port = 5432, timeoutMs = 30_000) {
  // підключення до бази даних
}

connect("db.internal");              // типовий порт і timeout
connect("db.internal", 5433);        // інший порт
connect("db.internal", 5432, 5_000); // коротший timeout
```

Якщо більшість викликів користується типовим портом і часом очікування, їм досить передати адресу. Незвичний сценарій може перевизначити потрібне значення. Типові значення прибирають зайві параметри зі звичайного виклику, але мають відповідати реальним потребам системи.

^aphsd-defaults-own-example

## Ознаки в коді

- Звичайний виклик працює без довгого списку параметрів.
- Модуль сам визначає значення, для яких уже має достатньо даних.
- Особливий сценарій можна налаштувати, не ускладнюючи звичайний.

## Межі та застосування

Типове значення корисне, коли воно підходить для звичайного випадку. Якщо правильне значення залежить від потреб користувача, треба дати йому можливість його вказати.

Це називають частковим приховуванням: налаштування існує, але більшості користувачів не потрібно про нього думати.

> [!tip] Як перевірити
> Чи змушую я кожного задавати значення, яке модуль уже може правильно вибрати сам?

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-08-pull-complexity-downwards#^aphsd-ch08-configuration|Розділ 8 — конфігурація та автоматичний вибір значень]]

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-defaults|Розділ 5 — Defaults and overexposure]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-leakage-couples-modules|Витік інформації зв’язує модулі спільним рішенням]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-temporal-decomposition-duplicates-knowledge|Часова декомпозиція дублює знання]]
- [[02-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
