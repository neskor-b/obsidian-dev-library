---
type: map
scope: "topic-map"
sources:
  - "clean-architecture"
title: "SOLID та принципи Clean Architecture"
aliases:
  - "SOLID organizes modules for change"
  - "SOLID principles map"
tags:
  - map
created: 2026-09-24
updated: 2026-09-24
---

# SOLID та принципи Clean Architecture

## Навіщо ця мапа

`SOLID` описує, як будувати модулі, класи та інші групування функцій і даних так, щоб система краще переносила зміни. Сенс цього набору принципів не в прихильності до `OOP` як стилю, а в тому, щоб на середньому рівні дизайну тримати відповідальності чіткими, контракти сумісними, інтерфейси вузькими, розширення передбачуваними, а деталі підлеглими політикам. Ця мапа збирає докупи п'ять принципів, розділи книги, з яких вони виведені, і спільні концепти й плейбук, що з них виросли.

^solid-organizes-modules-for-change-definition

## П'ять принципів

- `S` -> [[02-Concepts/single-responsibility-means-one-actor|SRP означає одного актора, а не одну дію]]
- `O` -> [[02-Concepts/open-closed-protects-high-level-policy|OCP захищає high-level policy через ієрархію залежностей]]
- `L` -> [[02-Concepts/liskov-substitution-preserves-client-behavior|LSP зберігає поведінку клієнта при підстановці]]
- `I` -> [[02-Concepts/interface-segregation-avoids-dependencies-on-unused-operations|ISP ізолює клієнтів від невикористаних операцій]]
- `D` -> [[02-Concepts/dependency-inversion|Інверсія залежностей]]

## Розділи книги

- [[01-Sources/books/clean-architecture/02-Chapters/ch-p3-design-principles|Частина III. Принципи дизайну]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-07-single-responsibility-principle|Розділ 7. Принцип єдиної відповідальності]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-08-open-closed-principle|Розділ 8. Принцип відкритості-закритості]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-09-liskov-substitution-principle|Розділ 9. Принцип підстановки Лісков]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-10-interface-segregation-principle|Розділ 10. Принцип розділення інтерфейсів]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-11-dependency-inversion-principle|Розділ 11. Принцип інверсії залежностей]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p4-component-principles|Частина IV. Принципи компонентів]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-12-components|Розділ 12. Компоненти]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion|Розділ 13. Зв'язність компонентів]]

## Суміжні концепти

- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[02-Concepts/component-cohesion-balances-release-change-and-reuse|Зв'язність компонентів балансує реліз, змінюваність і повторне використання]]
- [[02-Concepts/plugin-architecture-via-polymorphism|Поліморфізм дозволяє будувати plugin architecture]]

## Плейбук

- [[04-Playbooks/playbook-solid-in-code|Як дотримуватись SOLID у коді]]
