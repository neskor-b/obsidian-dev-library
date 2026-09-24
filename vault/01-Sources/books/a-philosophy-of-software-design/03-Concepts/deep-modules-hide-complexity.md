---
type: concept
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources:
  - "a-philosophy-of-software-design"
title: "Глибокі модулі приховують складність"
aliases:
  - "Deep modules hide complexity"
  - "Module depth"
tags:
  - source-note
  - concept
created: 2026-07-26
updated: "2026-09-24"
source: "chapter-4-5-6-7-and-9-excerpts"
---

# Глибокі модулі приховують складність

## Визначення

**Глибокий модуль робить багато корисної роботи, але користуватися ним просто.** Модуль — це клас, бібліотека або інша частина програми. Його інтерфейс — операції, які можна викликати, та правила їх використання.

^aphsd-deep-modules-definition

## Простий приклад

Порівняймо два способи отримати номер сторінки із запиту. Це спрощений навчальний приклад:

```java
// Код сам отримує рядок і перетворює його на число.
String value = request.getParams().get("page");
int page = Integer.parseInt(value);

// Модуль сам знаходить параметр і перетворює його на число.
int page = request.getIntParameter("page");
```

У другому варіанті модуль бере більше роботи на себе. Коду, який його викликає, достатньо вказати назву параметра. Не потрібно знати, як параметри зберігаються всередині.

Правила помилок усе одно треба знати: наприклад, що буде, якщо `page` відсутній або містить текст замість числа. Простий інтерфейс має бути зрозумілим, а не приховувати потрібні правила.

## Чому це важливо

Коли бібліотека сама виконує складні кроки, їх не потрібно повторювати в кожному місці використання. Зміни цих кроків також можна зробити всередині бібліотеки.

«Глибина» не вимірюється кількістю рядків коду. Важливо, скільки роботи модуль бере на себе і скільки знань вимагає від того, хто ним користується. Навіть один метод може бути складним у використанні, якщо він має багато незрозумілих параметрів і правил.

## Ознаки в коді

- Потрібний результат можна отримати кількома зрозумілими викликами.
- Модуль сам виконує внутрішні кроки та обробляє особливі випадки.
- Внутрішній алгоритм можна змінити, зберігши спосіб використання.
- Рідкісні налаштування не заважають звичайному сценарію.

> [!note] Що таке поверхневий модуль
> Це модуль, який бере на себе мало роботи, але додає нові виклики й правила, які потрібно вивчити. Наприклад, клас лише віддає внутрішню колекцію, а всю обробку залишає тому, хто його викликає. Для окремого класу має бути зрозуміла користь.

## Де ще в книзі проявляється глибина

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-main-idea|Розділ 5]] — модуль стає глибшим, коли збирає пов'язані правила всередині (HTTP-приклад: отримання й розбір запиту разом).
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-06-general-purpose-modules-are-deeper#^aphsd-ch06-text-api|Розділ 6]] — `delete(start, end)` замінює вузькі методи, але надто вузький метод (видалення одного символу) перекладає роботу на клієнта.
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-07-different-layer-different-abstraction#^aphsd-ch07-interface-implementation|Розділ 7]] — глибина це різниця між обіцянкою API і реалізацією; простий проксі-виклик такої різниці не створює.
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart#^aphsd-ch09-splitting-methods|Розділ 9.8]] — глибина не залежить від довжини методу: довгий метод із простою сигнатурою теж глибокий.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-main-idea]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-depth]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-unix]]

## Пов'язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/abstractions-must-preserve-important-details|Абстракції мають зберігати важливі деталі]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-classitis|Розділ 4 — Classitis]]

## Пов'язаний код

- У розділі 4 файлові операції Unix показують, як кілька операцій можуть приховати складну роботу зі зберіганням. Приклад потоків Java показує незручність, коли для звичайного читання потрібно вручну поєднувати кілька об’єктів.
