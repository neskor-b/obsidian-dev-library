---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "12"
title: "Компоненти"
aliases:
  - "Components"
tags:
  - source-note
  - chapter
created: 2026-04-21
updated: 2026-04-21
source: "excerpt"
---

# Компоненти

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 12
- Тип джерела: уривок

## Головна ідея

У цьому розділі Мартін дає дуже практичне визначення компонента: це найменша одиниця розгортання в системі. Компонентом може бути `jar`, `gem`, `DLL`, набір бінарних модулів або навіть агрегат вихідних файлів в інтерпретованій мові. Головна вимога не у форматі пакування, а в тому, щоб добре спроєктований компонент зберігав здатність до `independent deployability` і, як наслідок, до `independent developability`. Історичний екскурс від абсолютних адрес до сучасних плагінів показує, що така архітектура стала повсякденною лише тоді, коли лінкування й завантаження перестали бути дорогим вузьким місцем.

^clean-architecture-ch12-main-idea

## Ключові тези

- Компоненти - це units of deployment: найдрібніші сутності, які можна поставляти й розгортати як частину системи. ^clean-architecture-ch12-thesis-units-of-deployment
- Конкретна форма компонента залежить від екосистеми: у `Java` це `jar`, у `.NET` - `DLL`, у `Ruby` - `gem`, а в інтерпретованих мовах - агрегати source files. ^clean-architecture-ch12-thesis-language-forms
- Навіть якщо компоненти врешті склеюються в один executable, archive або runtime bundle, добре спроєктований компонент не втрачає принципової здатності бути незалежно розроблюваним і розгортаним. ^clean-architecture-ch12-thesis-independent-deployability
- У ранніх системах бібліотеки часто існували як source code, який просто додавали до application program, бо програми не були relocatable. ^clean-architecture-ch12-thesis-source-libraries
- Компілятори й loaders еволюціонували від fixed-address binaries до relocatable binaries з external references та external definitions; саме це дозволило незалежно компілювати й потім зв'язувати окремі частини системи. ^clean-architecture-ch12-thesis-relocatability
- Коли програми виросли, load-time linking став надто повільним, тому linking відокремили в окремий крок через linker, який створював готовий linked relocatable executable. ^clean-architecture-ch12-thesis-linker
- У 1990-х швидкість дисків, пам'яті й процесорів знову зробила load-time linking практичним, і на цьому тлі plugin architecture стала буденною моделлю розширення систем. ^clean-architecture-ch12-thesis-plugins-return
- Сучасні `jar`, shared libraries і `DLL`-plugins є не просто зручним форматом пакування, а наслідком довгої еволюції способів компіляції, лінкування та розгортання. ^clean-architecture-ch12-thesis-historical-continuity

## Історична траєкторія

- Нерелокований код: програма й бібліотека прив'язані до конкретних адрес у пам'яті, а library source часто компілюється разом із застосунком. ^clean-architecture-ch12-history-fixed-address
- Бінарна бібліотека на відомій адресі: окрема компіляція скорочує час build-циклу, але пам'ять фрагментується, а програма мусить "оббігати" library segment. ^clean-architecture-ch12-history-known-address
- Relocatable binaries + linking loader: loader може класти модулі один за одним, пересувати адреси й резолвити зовнішні символи. ^clean-architecture-ch12-history-linking-loader
- Окремий linker: повільне зв'язування виноситься в окремий крок, а запуск пришвидшується через уже підготовлений executable. ^clean-architecture-ch12-history-separate-linker
- Runtime plugins: коли link/load стали досить швидкими, динамічно зв'язувані `jar` і shared libraries знову стали практичними. ^clean-architecture-ch12-history-plugins

## Спрощена схема

```mermaid
flowchart LR
    src["Source library<br/>included in program"] --> fixed["Fixed-address binary<br/>non-relocatable"]
    fixed --> reloc["Relocatable binaries<br/>with external refs/defs"]
    reloc --> linker["Separate linker<br/>prepares executable"]
    linker --> plugins["Runtime-linked plugins<br/>jar / DLL / shared lib"]
```

Схема показує не "покращення заради покращення", а рух до дедалі кращої незалежності між частинами системи. Що дешевше й надійніше можна збирати, лінкувати та підключати окремі частини, то реальнішою стає компонентна архітектура. ^clean-architecture-ch12-simple-diagram-evolution

## Практичне читання для архітектури

- Думай про компонент не як про namespace чи папку, а як про межу складання й розгортання.
- Якщо компонент існує лише як логічна група класів, але не має навіть принципової незалежності у build/deploy циклі, його архітектурна межа може бути слабкою.
- Коли `UI`, інтеграції або storage можна підключати як окремі артефакти, архітектура легше підтримує експерименти й еволюцію деталей без переписування ядра.
- Plugin architecture стає практичною не лише через `DIP`, а й через те, що tooling та runtime достатньо швидкі, щоб така модульність не вбивала workflow.

## Важливі цитати

> Components are the units of deployment.

^clean-architecture-ch12-quote-units

> well-designed components always retain the ability to be independently deployable

^clean-architecture-ch12-quote-independent-deployability

## Пов'язані концепти

- [[02-Concepts/plugin-architecture-via-polymorphism|Поліморфізм дозволяє будувати plugin architecture]]
- [[02-Concepts/dependency-inversion|Інверсія залежностей]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming|Розділ 5. Об'єктно-орієнтоване програмування]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-p4-component-principles|Вступ до Part IV]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-11-dependency-inversion-principle|Попередній розділ: Принцип інверсії залежностей]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion|Наступний розділ: Зв'язність компонентів]]

## Пов'язані нотатки

- [[02-Concepts/plugin-architecture-via-polymorphism#^plugin-architecture-via-polymorphism-definition|Спільний концепт про plugin architecture]]
