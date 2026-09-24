---
type: map
scope: "topic-map"
sources:
  - "a-philosophy-of-software-design"
title: "Складність у дизайні ПЗ"
aliases:
  - "Complexity in software design map"
tags:
  - map
created: 2026-09-24
updated: 2026-09-24
---

# Складність у дизайні ПЗ

## Навіщо ця мапа

"A Philosophy of Software Design" будує майже всю аргументацію навколо однієї осі: складність — це не розмір системи, а труднощі розуміння й зміни, і вона накопичується малими кроками, якщо її свідомо не стримувати. Ця мапа збирає дев'ять розділів книги і всі концепти, що з них виросли, під одним дахом, щоб не губити зв'язок між загальною тезою і її конкретними механізмами (глибокі модулі, приховування інформації, red flags).

## Розділи книги

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-01-introduction-complexity|Розділ 1. Вступ: усе зводиться до складності]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity|Розділ 2. Природа складності]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming|Розділ 3. Робочого коду недостатньо: стратегічне й тактичне програмування]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep|Розділ 4. Модулі мають бути глибокими]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage|Розділ 5. Приховування інформації та її витік]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-06-general-purpose-modules-are-deeper|Розділ 6. Модулі загального призначення є глибшими]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-07-different-layer-different-abstraction|Розділ 7. Різні шари — різні абстракції]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-08-pull-complexity-downwards|Розділ 8. Перенось складність усередину модуля]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart|Розділ 9. Разом чи окремо?]]

## Умбрелла-концепти (shared)

- [[02-Concepts/complexity-is-the-central-design-problem|Складність є центральною проблемою дизайну ПЗ]]
- [[02-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]

## Локальні механізми (source-local)

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/design-is-continuous-and-incremental|Дизайн є безперервним та інкрементальним]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/complexity-accumulates-incrementally|Складність накопичується інкрементально]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/red-flags-guide-design-judgment|Red flags спрямовують дизайнерське судження]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/abstractions-must-preserve-important-details|Абстракції мають зберігати важливі деталі]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-leakage-couples-modules|Витік інформації зв'язує модулі спільним рішенням]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-temporal-decomposition-duplicates-knowledge|Часова декомпозиція дублює знання]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-defaults-hide-uncommon-options|Типові значення приховують рідкісні налаштування]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-shared-settings|Спільні налаштування без передачі через кожен метод]]

## Суміжна архітектурна тема

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]] — та сама економіка складності, застосована до архітектурних рішень у Clean Architecture.
