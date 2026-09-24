---
type: concept
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources:
  - "a-philosophy-of-software-design"
title: "Складність накопичується інкрементально"
aliases:
  - "Complexity is incremental"
tags:
  - source-note
  - concept
created: 2026-07-26
updated: 2026-09-24
source: "chapter-2-excerpt"
---

# Складність накопичується інкрементально

## Визначення

Складність рідко виникає через одну катастрофічну помилку. Вона накопичується з багатьох малих залежностей і неочевидностей, кожна з яких окремо здається прийнятною, але разом вони починають впливати майже на кожну зміну в системі.

^aphsd-complexity-incremental-definition

## Чому це важливо

Локальний ефект чергового компромісу надто малий, щоб одразу виправдати прибирання, а виправлення одного старого недоліку надто мале, щоб помітно оздоровити вже складну систему. Ця асиметрія пояснює, чому складність легко додавати й важко усувати та чому дисципліна потрібна під час кожної зміни.

## Приклад

Один розробник додає параметр `retries=0` до `fetchUser`, бо один клієнт іноді отримує timeout. Інший додає `useCache=false`, бо окремому запиту потрібні свіжі дані. Згодом з'являється `skipValidation=true` для внутрішнього скрипта. Кожен параметр окремо здається невеликим, але їхні комбінації й взаємодії стають частиною контракту. Після наступних подібних змін новому розробнику вже доводиться читати реалізацію, щоб зрозуміти, які поєднання безпечні.

^aphsd-complexity-incremental-example

## Ознаки в коді

- Нові special cases регулярно додаються як «тимчасові» винятки.
- Кожна окрема залежність здається нешкідливою, але типові зміни вже перетинають багато таких зв'язків.
- Окремий рефакторинг майже не змінює загальної підтримуваності, бо проблеми розподілені системою.
- Команда виправдовує нову неочевидність тим, що її поточна вартість невелика.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-thesis-incremental]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-quote-incremental]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity#^aphsd-ch02-rule-zero-tolerance]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-thesis-patch-cycle]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming#^aphsd-ch03-rule-fix-now]]

## Пов'язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]
- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]

## Пов'язаний код

- Окремі code notes для цього концепту ще не створені.

## Пов'язані playbooks

- Окремий playbook із цього уривка не створено.
