---
type: concept
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
scope: "source-local"
sources:
  - "a-philosophy-of-software-design"
title: "Red flags спрямовують дизайнерське судження"
aliases:
  - "Red flags guide design judgment"
  - "Recognize signs of unnecessary complexity"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-09-24
source: "chapter-1-excerpt"
---

# Red flags спрямовують дизайнерське судження

## Визначення

Red flags у цій книзі - це впізнавані симптоми того, що код став складнішим, ніж потрібно. Вони не дають готового рецепта правильного дизайну, але змушують зупинитися, поставити під сумнів поточну форму рішення й пошукати альтернативу з меншим когнітивним навантаженням.

^aphsd-red-flags-definition

## Чому це важливо

Новачок рідко одразу бачить красивий дизайн, зате може навчитися помічати тривожні сигнали. Через це red flags стають практичним мостом між абстрактними принципами й щоденною роботою: вони вчать розпізнавати момент, коли варто не латати код, а переосмислити його форму.

## Ознаки в коді

- Пояснення поведінки вимагає дедалі більше винятків, special cases і фраз на кшталт "окрім випадку, коли...".
- Щоб безпечно змінити локальну частину системи, потрібно знати багато неочевидних деталей з інших модулів.
- Code review регулярно знаходить одну й ту саму структурну проблему в різних місцях.
- **Повторення (Repetition, розділ 9.3):** той самий (або майже той самий) фрагмент коду повторюється знову й знову — сигнал, що правильну абстракцію ще не знайдено.
- **Змішування загального та спеціального (Special-General Mixture, розділ 9.4):** загальний механізм містить код, спеціалізований під один конкретний випадок використання; це створює витік інформації між механізмом і випадком використання.
- **Зрощені методи (Conjoined Methods, розділ 9.8):** неможливо зрозуміти реалізацію одного методу чи фрагмента, не читаючи інший — вони піддаються розумінню лише разом.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-thesis-red-flags]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity#^aphsd-ch01-quote-red-flags]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart#^aphsd-ch09-duplication|Розділ 9.3 — Repetition]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart#^aphsd-ch09-general-special|Розділ 9.4 — Special-General Mixture]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart#^aphsd-conjoined-methods-flag|Розділ 9.8 — Conjoined Methods]]

## Пов'язані концепти

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]

## Пов'язаний код

- Окремі code notes для цього концепту ще не створені.
