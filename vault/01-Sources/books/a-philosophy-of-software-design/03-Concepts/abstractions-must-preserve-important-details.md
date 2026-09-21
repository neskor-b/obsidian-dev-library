---
type: concept
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources:
  - "a-philosophy-of-software-design"
title: "Абстракції мають зберігати важливі деталі"
aliases:
  - "Abstractions must preserve important details"
  - "False abstraction"
tags:
  - source-note
  - concept
created: 2026-07-26
updated: 2026-09-21
source: "chapter-4-and-5-excerpts"
---

# Абстракції мають зберігати важливі деталі

## Визначення

Абстракція є спрощеним поглядом на сутність: вона приховує деталі, неважливі для користувача, але залишає видимими всі факти, потрібні для коректного використання. Якщо вона показує зайве — зростає когнітивне навантаження; якщо приховує необхідне — виникає оманлива, або false, абстракція.

^aphsd-abstraction-important-details-definition

## Чому це важливо

Простота інтерфейсу не є самоціллю. У файловій системі користувачеві неважливий алгоритм розміщення блоків, але для бази даних критично знати, коли запис справді потрапив на стале сховище. Якісна абстракція мінімізує саме кількість важливих для клієнта знань, а не просто кількість видимих деталей.

## Ознаки в коді

- Контракт явно описує поведінку, обмеження, побічні ефекти та необхідний порядок операцій.
- Деталі реалізації не просочуються в кожен клієнтський модуль.
- Клієнт може передбачити важливі наслідки без читання реалізації.
- Неформальна частина контракту узгоджена з формальними сигнатурами й тестами.

> [!warning] Оманлива простота
> Якщо для безпечного використання API все одно треба читати його реалізацію, важливі деталі не зникли — вони лише стали неочевидними.

## Уточнення з розділу 5

Розділ 5 окреслює межу приховування: параметри, які потрібно змінювати для різних сценаріїв, мають залишатися доступними, якщо модуль не може належно налаштуватися автоматично.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-limits|Розділ 5]]


- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-informal-interface]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-thesis-abstraction]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-04-modules-should-be-deep#^aphsd-ch04-rule-important-details]]

## Пов'язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/dependencies-and-obscurity|Залежності та неочевидність породжують складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]

## Пов'язаний код

- Правила flush/fsync у файлових системах ілюструють деталь реалізації, яка стає частиною контракту для надійного збереження даних.
