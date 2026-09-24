---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
title: "SOLID організовує модулі для змінюваності"
aliases:
  - "SOLID organizes modules for change"
  - "SOLID principles shape mid-level design"
tags:
  - source-note
  - concept
created: 2026-04-14
updated: 2026-04-18
source: "synthesis"
---

# SOLID організовує модулі для змінюваності

## Визначення

`SOLID` описує, як будувати модулі, класи та інші групування функцій і даних так, щоб система краще переносила зміни. Сенс цього набору принципів не в прихильності до `OOP` як стилю, а в тому, щоб на середньому рівні дизайну тримати відповідальності чіткими, контракти сумісними, інтерфейси вузькими, розширення передбачуваними, а деталі підлеглими політикам.

^solid-organizes-modules-for-change-definition

## Чому це важливо

Цей концепт закриває проміжок між "чистим кодом" і "гарною архітектурою". Без нього окремі добре написані модулі легко перетворюються на хаотичну систему зі сплутаними залежностями й нечіткими причинами змін. `SOLID` дає словник для перевірки саме форми модулів: чи не змішані в них ролі, чи можна їх розширювати без постійного ламання, чи не тягнуть вони зайві залежності й чи не підпорядковані політики випадковим деталям.

## Ознаки в коді

- Кожен модуль має достатньо чітку причину для зміни, пов'язану з конкретною роллю, актором або політикою.
- Нові сценарії переважно додаються через нові реалізації, адаптери або розширення контрактів, а не через редагування стабільного ядра в багатьох місцях.
- Клієнти залежать від вузьких інтерфейсів, а high-level policy не імпортує інфраструктурні деталі напряму.

## Принципи SOLID

- `S` -> [[02-Concepts/single-responsibility-means-one-actor|SRP означає одного актора, а не одну дію]]
- `O` -> [[02-Concepts/open-closed-protects-high-level-policy|OCP захищає high-level policy через ієрархію залежностей]]
- `L` -> [[02-Concepts/liskov-substitution-preserves-client-behavior|LSP зберігає поведінку клієнта при підстановці]]
- `I` -> [[02-Concepts/interface-segregation-avoids-dependencies-on-unused-operations|ISP ізолює клієнтів від невикористаних операцій]]
- `D` -> [[02-Concepts/dependency-inversion|Інверсія залежностей]]

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles#^clean-architecture-p3-main-idea]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles#^clean-architecture-p3-thesis-mid-level]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles#^clean-architecture-p3-thesis-five-principles]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles#^clean-architecture-p3-quote-dip]]

## Пов'язані концепти

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[02-Concepts/dependency-inversion|Інверсія залежностей]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-01-design-and-architecture|Розділ 1. Що таке дизайн і архітектура]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming|Розділ 5. Об'єктно-орієнтоване програмування]]

## Пов'язаний код

- Конкретні code notes для цього спільного концепту ще не додані.
