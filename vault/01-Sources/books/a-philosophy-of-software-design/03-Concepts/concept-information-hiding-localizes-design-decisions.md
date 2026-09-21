---
type: "concept"
scope: "source-local"
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
sources: ["a-philosophy-of-software-design"]
title: "Приховування інформації локалізує проєктні рішення"
aliases: ["Information hiding"]
tags: ["source-note", "concept"]
created: "2026-09-21"
updated: "2026-09-21"
source: "chapter-5-excerpt"
---

# Приховування інформації локалізує проєктні рішення

## Визначення

Приховування інформації означає, що модуль володіє певними проєктними рішеннями, а його користувачам не потрібно знати ці рішення. Прихованими можуть бути структури даних, алгоритми, розміри сторінок і навіть припущення про типове навантаження.

^aphsd-hiding-definition

## Чому це важливо

Це одночасно зменшує кількість понять для клієнта й локалізує зміни реалізації. Позначка `private` сама по собі цього не забезпечує: getter, що повертає внутрішню структуру, може розкрити те саме знання через публічний API.

## Ознаки в коді

- Клієнт отримує потрібний результат, не керуючи внутрішніми кроками.
- Заміна структури даних не вимагає переписування клієнтів.
- Приватні методи приховують окремі можливості навіть від решти класу; поля використовуються в мінімально потрібній кількості місць.

## Межі та застосування

Не слід приховувати параметри, які клієнт мусить налаштовувати для свого сценарію. Спершу варто спробувати автоматичний вибір; якщо цього недостатньо, потрібна явна частина контракту.

## Джерела

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage#^aphsd-ch05-hiding|Розділ 5 — Information hiding]]

## Пов’язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-information-leakage-couples-modules|Витік інформації зв’язує модулі спільним рішенням]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-temporal-decomposition-duplicates-knowledge|Часова декомпозиція дублює знання]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/concept-defaults-hide-uncommon-options|Типові значення приховують рідкісні налаштування]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
