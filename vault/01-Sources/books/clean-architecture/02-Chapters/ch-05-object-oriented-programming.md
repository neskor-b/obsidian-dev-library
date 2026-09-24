---
type: chapter
source_type: "books"
source_slug: "clean-architecture"
source_title: "Clean Architecture"
chapter: "5"
title: "Об'єктно-орієнтоване програмування"
aliases:
  - "Object-Oriented Programming"
tags:
  - source-note
  - chapter
created: 2026-03-24
updated: 2026-04-18
source: "excerpt"
---

# Об'єктно-орієнтоване програмування

## Контекст

- Джерело: [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Clean Architecture]]
- Розділ: 5
- Тип джерела: уривок

## Головна ідея

У цьому розділі Роберт Мартін відкидає популярні, але поверхові визначення `object-oriented programming` через "поєднання даних і функцій", "моделювання реального світу" або магічну трійку `encapsulation`, `inheritance`, `polymorphism`. Його архітектурна теза значно конкретніша: головна сила `OO` у тому, що воно робить поліморфізм безпечним і буденним, а отже дозволяє розвертати напрямок залежностей, відокремлювати політики від деталей і будувати системи, у яких `UI`, база даних та інші низькорівневі частини стають плагінами до бізнес-правил.

^clean-architecture-ch05-main-idea

## Ключові тези

- Визначення `OO` як "поєднання даних і функцій" або як "моделювання реального світу" не пояснюють його інженерну цінність і лише маскують суть. ^clean-architecture-ch05-thesis-false-definitions
- `Encapsulation` не є унікальним здобутком `OO`: у `C` можна було приховати структуру даних через `header` і `implementation` навіть сильніше, ніж у класичному `C++`. ^clean-architecture-ch05-thesis-encapsulation
- `Inheritance` теж не було абсолютною новинкою: програмісти `C` уже використовували сумісне розташування полів у `struct`, щоб одна структура могла маскуватися під іншу; `OO` радше зробило цей прийом зручнішим і безпечнішим. ^clean-architecture-ch05-thesis-inheritance
- Поліморфна поведінка існувала задовго до `OO` через вказівники на функції та однакові сигнатури, але такі домовленості були крихкими й вимагали ручної дисципліни. ^clean-architecture-ch05-thesis-polymorphism-history
- Справжня сила `OO` у тому, що воно нав'язує дисципліну непрямому передаванню керування: виклики проходять через абстракції, а не через жорстке знання деталей. ^clean-architecture-ch05-thesis-indirect-control
- Завдяки цьому низькорівневі елементи можуть ставати плагінами до стабільнішого ядра, так само як `IO`-пристрої в `UNIX` підключаються до програми копіювання без її переписування. ^clean-architecture-ch05-thesis-plugins
- Поліморфізм дає архітектору контроль над напрямком залежностей у вихідному коді: `source code dependencies` можна розвернути так, щоб `UI` і база даних залежали від бізнес-правил, а не навпаки. ^clean-architecture-ch05-thesis-dependency-inversion
- Коли деталі залежать від політик, компоненти можна збирати, розгортати й розвивати незалежно; звідси випливають `independent deployability` та `independent developability`. ^clean-architecture-ch05-thesis-independent-components

## Приклад коду

### Вказівники на функції в C як основа поліморфізму

```c showLineNumbers
struct FILE {
  void (*open)(char* name, int mode);
  void (*close)();
  int (*read)();
  void (*write)(char);
  void (*seek)(long index, int mode);
};

extern struct FILE* STDIN;

int getchar() {
  return STDIN->read();
}
```

^clean-architecture-ch05-code-function-pointers

Цей фрагмент показує, що поліморфізм не народився разом із `OO`-мовами. Поведінка `getchar()` змінюється залежно від того, на який `FILE` вказує `STDIN`, а отже виклик проходить через таблицю функціональних вказівників. Ідея така сама, як у `virtual method` та `vtable`: стабільний виклик у коді делегує конкретну поведінку змінній реалізації.

У чистому `C` цей підхід тримається на ручних домовленостях: треба правильно ініціалізувати всі функціональні вказівники й завжди викликати поведінку саме через них. Якщо структура контракту змінюється або один із вказівників лишається неініціалізованим, помилка буде низькорівневою й важкою для локалізації.

## Важливі цитати

> OO imposes discipline on indirect transfer of control.

^clean-architecture-ch05-quote-discipline

> OO is the ability, through the use of polymorphism, to gain absolute control over every source code dependency in the system.

^clean-architecture-ch05-quote-definition

## Пов'язані концепти

- [[01-Sources/books/clean-architecture/02-Chapters/ch-03-paradigm-overview|Розділ 3. Огляд парадигм]]
- [[02-Concepts/dependency-inversion|Інверсія залежностей]]
- [[02-Concepts/plugin-architecture-via-polymorphism|Поліморфізм дозволяє будувати plugin architecture]]

## Джерело та продовження

- [[01-Sources/books/clean-architecture/Clean Architecture (Robert C. Martin)|Нотатка книги]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-04-structured-programming|Попередній розділ: Структурне програмування]]

## Пов'язані нотатки

- [[02-Concepts/dependency-inversion#^dependency-inversion-definition|Спільний концепт про розворот залежностей]]
- [[02-Concepts/plugin-architecture-via-polymorphism#^plugin-architecture-via-polymorphism-definition|Спільний концепт про плагінну архітектуру]]
