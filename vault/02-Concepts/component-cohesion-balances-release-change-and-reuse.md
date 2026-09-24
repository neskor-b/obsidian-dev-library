---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
title: "Зв'язність компонентів балансує реліз, змінюваність і повторне використання"
aliases:
  - "Component cohesion balances release, change, and reuse"
  - "REP CCP CRP"
tags:
  - source-note
  - concept
created: 2026-04-21
updated: 2026-09-24
source: "synthesis"
---

# Зв'язність компонентів балансує реліз, змінюваність і повторне використання

## Визначення

Зв'язність компонента визначається не одним критерієм, а балансом трьох сил. `REP` перевіряє, чи справді межа компонента збігається з межею релізу й версіонування. `CCP` перевіряє, чи зібрані разом класи, які змінюються з тих самих причин. `CRP` перевіряє, чи не примушує компонент клієнтів залежати від непотрібних класів. Добрий компонент тримає ці сили в напрузі так, щоб і зміну локалізувати, і reuse не робити токсичним, і release story лишати осмисленою.

^component-cohesion-definition

## Чому це важливо

Цей концепт переводить розмову про "гарне групування класів" у площину експлуатаційної вартості. Погана компонентна межа проявляється не лише в неохайній структурі директорій, а в тому, що зміни розповзаються по кількох артефактах, клієнти тягнуть зайвий baggage, а релізи стають семантично мутними. Саме тому cohesion компонентів пов'язана з реальною вартістю зміни не менше, ніж локальні `SOLID`-рішення.

## Три перевірки межі компонента

- `REP`: якщо класи не мають природного спільного release cycle, їм, імовірно, не місце в одному компоненті.
- `CCP`: якщо класи майже завжди змінюються разом, їх розділення створює зайві redeploy і revalidation costs.
- `CRP`: якщо споживачі стабільно використовують лише частину компонента, а решта є випадковим вантажем, межа занадто широка.

## Як застосовувати

- Починай із векторів змін: дивися, які класи команда реально редагує разом.
- Потім перевір release story: чи буде зрозуміло користувачу компонента, чому саме ці зміни вийшли під однією версією.
- Після цього перевір reuse story: чи може залежний код чесно сказати, що йому потрібен увесь компонент, а не один випадковий клас.
- Переглядай межі з часом: на ранньому етапі проєкту природно тяжіти до `CCP`, а з появою зовнішніх споживачів і стабільних артефактів зростає тиск `REP` і `CRP`.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-main-idea]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-thesis-rep]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-thesis-ccp]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-thesis-crp]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-thesis-tension]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-thesis-maturity]]

## Пов'язані концепти

- [[02-Concepts/single-responsibility-means-one-actor|SRP означає одного актора, а не одну дію]]
- [[02-Concepts/interface-segregation-avoids-dependencies-on-unused-operations|ISP ізолює клієнтів від невикористаних операцій]]
- [[02-Concepts/open-closed-protects-high-level-policy|OCP захищає high-level policy через ієрархію залежностей]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-09-better-together-or-better-apart|Розділ 9. Разом чи окремо?]] — та сама ідея "групуй те, що змінюється разом", без формального `REP`/`CCP`/`CRP`-апарату.

## Пов'язаний фрагмент

- [[01-Sources/books/clean-architecture/02-Chapters/ch-13-component-cohesion#^clean-architecture-ch13-tension-diagram|Трикутник напруги між `REP`, `CCP` і `CRP`]]
