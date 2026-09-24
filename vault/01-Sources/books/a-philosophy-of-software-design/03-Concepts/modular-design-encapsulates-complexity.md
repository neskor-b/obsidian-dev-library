---
type: concept
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
scope: "source-local"
sources:
  - "a-philosophy-of-software-design"
title: "Модульний дизайн інкапсулює складність"
aliases:
  - "Modular design encapsulates complexity"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-09-24
source: "chapters-1-and-4-excerpts"
---

# Модульний дизайн інкапсулює складність

## Визначення

Модульний дизайн не усуває всю складність системи, але обмежує площу контакту з нею. Система ділиться на відносно незалежні модулі, кожен з яких приховує внутрішні рішення настільки, щоб розробник міг змінювати один модуль без потреби тримати в голові деталі решти системи.

^aphsd-modular-design-definition

## Чому це важливо

Ця ідея переводить боротьбу зі складністю з рівня "зробімо все простим" до більш реалістичного питання: яку складність ми не можемо прибрати, але можемо якісно локалізувати. Без такого локалізування масштаб системи швидко перевищує когнітивні межі команди.

Межа модуля розділяє інтерфейс і реалізацію. Розробник має знати реалізацію модуля, над яким працює, та інтерфейси його залежностей, але не внутрішній устрій цих залежностей. Чим менше знань переходить через межу, тим менше змін поширюється системою.

## Приклад

`BillingModule` обчислює суму з урахуванням тарифів, округлення й податків. `PaymentsModule` виконує списання, приховуючи інтеграцію з провайдером, повторні спроби й ідемпотентність. `BillingModule` передає узгоджену суму через `PaymentsModule.charge(amount)` і не знає, який провайдер обробляє платіж. Заміна провайдера лишається всередині `PaymentsModule`, якщо контракт списання та його поведінка зберігаються.

^aphsd-modular-design-example

## Ознаки в коді

- Модуль має чітку межу та інтерфейс, який не змушує читача знати його внутрішній устрій.
- Внесення змін у модуль рідко вимагає каскаду синхронних змін в інших частинах системи.
- Внутрішні special cases і технічні деталі не витікають назовні через API, імена або протоколи взаємодії.
- Неформальні правила використання — поведінка, порядок викликів, обмеження — явно вважаються частиною інтерфейсу.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-two-approaches]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-main-idea]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-interface-implementation]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-informal-interface]]

## Пов'язані концепти

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]
- [[02-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/abstractions-must-preserve-important-details|Абстракції мають зберігати важливі деталі]]

## Пов'язаний код

- Окремі code notes для цього концепту ще не створені.
