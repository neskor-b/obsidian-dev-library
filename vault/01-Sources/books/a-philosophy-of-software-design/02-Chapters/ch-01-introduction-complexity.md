---
type: chapter
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
chapter: "1"
title: "Вступ: усе зводиться до складності"
aliases:
  - "Introduction (It’s All About Complexity)"
  - "How to use this book"
tags:
  - source-note
  - chapter
created: 2026-03-24
updated: 2026-09-24
source: "excerpt"
---

# Вступ: усе зводиться до складності

## Контекст

- Джерело: [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|A Philosophy of Software Design]]
- Розділ: 1
- Тип джерела: уривок

## Головна ідея

Оустергут ставить складність у центр дизайну ПЗ: головна проблема не в тому, щоб змусити програму працювати один раз, а в тому, щоб система лишалася зрозумілою під час постійних змін. Хороший дизайн або прибирає зайву складність, або ізолює її межами модулів, а практичний спосіб навчитися цьому полягає в безперервному редизайні, code review і вмінні помічати red flags.

^aphsd-ch01-main-idea

## Ключові тези

- Найбільше обмеження в розробці ПЗ пов'язане з людською здатністю утримувати в голові систему, що постійно ускладнюється. ^aphsd-ch01-thesis-understanding
- Складність накопичується майже неминуче, а її наслідки проявляються як уповільнення розробки, помилки й зростання вартості змін. ^aphsd-ch01-thesis-accumulates
- Боротися зі складністю можна двома головними шляхами: спрощувати код і приховувати неминучі деталі за межами модулів. ^aphsd-ch01-thesis-two-approaches
- Для ПЗ дизайн не є одноразовою початковою фазою: incremental development вимагає постійного переосмислення та редизайну. ^aphsd-ch01-thesis-continuous-design
- Waterfall погано підходить для великих програмних систем, бо критичні вади дизайну часто видно лише під час реалізації. ^aphsd-ch01-thesis-waterfall
- Книгу варто читати поруч із code review: red flags у чужому коді допомагають тренувати власне дизайнерське судження. ^aphsd-ch01-thesis-red-flags

## Приклад: як одна «тимчасова» латка стає постійною складністю

Потрібно швидко додати знижку 10% для акції на вихідні. Розробник вставляє `if isWeekendPromo { price *= 0.9 }` прямо в `calculateTotal`. Для однієї акції цього досить.

Згодом з'являються знижки для нових покупців і гуртових замовлень. Умови накопичуються в тому самому методі; порядок їх застосування починає впливати на суму. Щоб додати наступну акцію, вже треба розібратися з усіма попередніми правилами. Кожен локальний компроміс здавався прийнятним, але їхня сума зробила метод складним для зміни.

^aphsd-ch01-example-weekend-discount

## Практичні правила

- Коли чергова зміна стає важкою для пояснення, спершу підозрюйте зайву складність, а не лише нестачу часу. ^aphsd-ch01-rule-complexity-first
- Якщо складність неможливо прибрати, сховайте її за межею модуля так, щоб інші частини системи працювали з простішою моделлю. ^aphsd-ch01-rule-hide-complexity
- Плануйте редизайн як нормальну частину розробки, а не як рідкісний "великий рефакторинг". ^aphsd-ch01-rule-redesign-normal
- Використовуйте code review не лише для пошуку помилок, а й для тренування зору на structural red flags. ^aphsd-ch01-rule-review-red-flags

## Важливі цитати

> Complexity increases inevitably over the life of any program.

^aphsd-ch01-quote-complexity

> Incremental development means that software design is never done.

^aphsd-ch01-quote-incremental

> One of the best ways to improve your design skills is to learn to recognize red flags.

^aphsd-ch01-quote-red-flags

## Пов'язані концепти

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/red-flags-guide-design-judgment|Red flags спрямовують дизайнерське судження]]

## Пов'язані приклади коду

- Окремі code notes для цього розділу ще не створені.

## Джерело та продовження

- [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|Нотатка книги]]
- Сирий уривок розділу 1 ще не збережений окремою нотаткою в `01-Inbox/`

## Пов'язані нотатки

- [[02-Concepts/complexity-is-the-central-design-problem#^complexity-central-design-problem-definition|Визначення складності як центральної проблеми дизайну]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity#^aphsd-modular-design-definition|Визначення модульного дизайну]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental#^aphsd-design-continuous-definition|Визначення безперервного дизайну]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/red-flags-guide-design-judgment#^aphsd-red-flags-definition|Визначення red flags]]
