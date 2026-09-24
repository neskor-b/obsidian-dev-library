---
type: chapter
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
chapter: "2"
title: "Природа складності"
aliases:
  - "The Nature of Complexity"
tags:
  - source-note
  - chapter
created: 2026-07-26
updated: 2026-07-26
source: "excerpt"
---

# Природа складності

## Контекст

- Джерело: [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|A Philosophy of Software Design]]
- Тип джерела: книга
- Розділ: 2
- Сегмент: 2.1–2.5

## Головна ідея

Складність ПЗ — це не розмір системи, а труднощі, які розробник відчуває, коли намагається її зрозуміти або змінити. Вона поступово виникає з залежностей і неочевидності, а проявляється через каскадні зміни, когнітивне навантаження та невідомі невідомості.

^aphsd-ch02-main-idea

## Ключові тези

- Складність треба оцінювати з позиції конкретного розробника, завдання й моменту часу, а не за кількістю функцій або рядків коду. ^aphsd-ch02-thesis-experience
- Внесок частини системи в загальну складність залежить і від її локальної складності, і від того, як часто розробники з нею працюють. ^aphsd-ch02-thesis-weighted
- Дизайн, зрозумілий автору, але складний для інших читачів, залишається складним; оцінка читача важливіша за відчуття автора. ^aphsd-ch02-thesis-reader
- Каскадні зміни, когнітивне навантаження та невідомі невідомості є трьома основними симптомами складності. ^aphsd-ch02-thesis-symptoms
- Залежності та неочевидність є двома основними причинами складності; дизайн має зменшувати їх або робити простими й явними. ^aphsd-ch02-thesis-causes
- Складність накопичується багатьма малими компромісами, тому контроль над нею потребує уваги під час кожної зміни. ^aphsd-ch02-thesis-incremental

## Практичні правила

- Оцінюйте дизайн за вартістю типових змін і обсягом знань, потрібних для них, а не за довжиною реалізації. ^aphsd-ch02-rule-cost
- Якщо складність неможливо усунути, локалізуйте її в рідко змінюваній частині системи. ^aphsd-ch02-rule-isolate
- Замінюйте приховані залежності на явні залежності через зрозумілий API, який легко знайти пошуком і перевірити інструментами. ^aphsd-ch02-rule-explicit-dependencies
- Коли іншим розробникам код здається складним, дослідіть причини розбіжності замість того, щоб покладатися на власну знайомість із реалізацією. ^aphsd-ch02-rule-listen-readers
- Не приймайте малу порцію зайвої складності лише тому, що її локальний ефект поки непомітний. ^aphsd-ch02-rule-zero-tolerance

## Важливі цитати

> Complexity is more apparent to readers than writers.

^aphsd-ch02-quote-readers

> Complexity isn’t caused by a single catastrophic error; it accumulates in lots of small chunks.

^aphsd-ch02-quote-incremental

## Пов'язані концепти

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/complexity-accumulates-incrementally|Складність накопичується інкрементально]]

## Пов'язані приклади коду

- Окремі code notes для цього розділу не створені.

## Джерело та продовження

- [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|Нотатка книги]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity|Розділ 1. Вступ: усе зводиться до складності]]

## Пов'язані нотатки

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
