---
type: chapter
source_type: "books"
source_slug: "a-philosophy-of-software-design"
source_title: "A Philosophy of Software Design"
chapter: "4"
title: "Модулі мають бути глибокими"
aliases:
  - "Modules Should Be Deep"
  - "Deep Modules"
tags:
  - source-note
  - chapter
created: 2026-07-26
updated: 2026-09-24
source: "excerpt"
---

# Модулі мають бути глибокими

## Контекст

- Джерело: [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|A Philosophy of Software Design]]
- Тип джерела: книга
- Розділ: 4
- Сегмент: 4.1–4.8

## Головна ідея

Найкращий модуль приховує значну функціональність і складність реалізації за малим, простим інтерфейсом. Його цінність визначається не малою кількістю рядків чи класів, а співвідношенням користі до складності, яку інтерфейс нав'язує решті системи.

^aphsd-ch04-main-idea

## Ключові тези

- Модульний дизайн зменшує частку загальної складності, з якою розробник мусить працювати одночасно, завдяки відносно незалежним модулям. ^aphsd-ch04-thesis-modularity
- Модуль складається з інтерфейсу та реалізації: користувач повинен розуміти контракт модуля, але не його внутрішній механізм. ^aphsd-ch04-thesis-interface-implementation
- Інтерфейс містить не лише формальні сигнатури, а й неформальні знання про поведінку, обмеження, порядок викликів і побічні ефекти. ^aphsd-ch04-thesis-informal-interface
- Абстракція корисна лише тоді, коли приховує неважливі деталі, але залишає видимими все, що потрібно для правильного використання. ^aphsd-ch04-thesis-abstraction
- Глибина модуля — це співвідношення вигоди до вартості: функціональність є вигодою, а складність інтерфейсу — вартістю для решти системи. ^aphsd-ch04-thesis-depth
- Unix file I/O є глибоким модулем: кілька стабільних системних викликів приховують величезну складність файлової системи, кешування, прав доступу та пристроїв. ^aphsd-ch04-thesis-unix
- Garbage collector ще глибший у сенсі видимого контракту: складна реалізація працює без окремого інтерфейсу звільнення пам'яті та навіть зменшує загальний інтерфейс системи. ^aphsd-ch04-thesis-gc
- Дрібні класи й методи часто є поверхневими: вони додають нові імена та контракти, але майже не приховують складності. ^aphsd-ch04-thesis-shallow
- Classitis локально спрощує окремі класи, але глобально збільшує кількість інтерфейсів, boilerplate і когнітивних переходів. ^aphsd-ch04-thesis-classitis
- Простий типовий сценарій важливіший за однакову видимість усіх можливостей: рідкісні опції мають бути доступними, але не обтяжувати звичайне використання. ^aphsd-ch04-thesis-common-case

## Практичні правила

- Оцінюйте модуль за тим, скільки складності він приховує на одиницю складності свого інтерфейсу. ^aphsd-ch04-rule-depth
- Включайте до аналізу інтерфейсу всі знання, потрібні клієнтові, а не лише типи та сигнатури. ^aphsd-ch04-rule-full-interface
- Приховуйте деталь лише після перевірки, що клієнтові вона справді не потрібна для коректності, надійності чи продуктивності. ^aphsd-ch04-rule-important-details
- Робіть типовий сценарій поведінкою за замовчуванням; рідкісні налаштування відокремлюйте так, щоб більшість користувачів могла їх не знати. ^aphsd-ch04-rule-common-case
- Не діліть клас або метод лише через його розмір: поділ виправданий, коли нова межа створює корисну абстракцію й зменшує загальну складність. ^aphsd-ch04-rule-no-size-threshold
- Не створюйте метод, якщо його назва й контракт вимагають стільки ж знань, скільки один очевидний вираз у місці виклику. ^aphsd-ch04-rule-no-empty-abstraction
- Під час API-review запитуйте не лише «чи все можливо зробити?», а й «скільки понять треба вивчити для найчастішого сценарію?». ^aphsd-ch04-rule-effective-complexity

## Важливі цитати

> The best modules are those whose interfaces are much simpler than their implementations.

^aphsd-ch04-quote-best-modules

> Interfaces are good, but more, or larger, interfaces are not necessarily better!

^aphsd-ch04-quote-interfaces

## Приклад: Unix файлові операції як глибокий модуль

Інтерфейс Unix `open`, `read`, `write`, `close` приховує розміщення даних, кешування, черги запису, права доступу й роботу з пристроями. Клієнт читає файл через невеликий набір операцій:

```c
int fd = open("data.txt", O_RDONLY);
char buf[1024];
ssize_t n = read(fd, buf, sizeof(buf));
if (n >= 0) { /* обробити n прочитаних байтів */ }
close(fd);
```

Поверхнева обгортка лише повторює наявний інтерфейс:

```java
import java.io.IOException;
import java.io.RandomAccessFile;

class FileWrapper implements AutoCloseable {
    private final RandomAccessFile file;
    FileWrapper(String path) throws IOException { file = new RandomAccessFile(path, "r"); }
    int read(byte[] buf) throws IOException { return file.read(buf); }
    public void close() throws IOException { file.close(); }
}
```

`FileWrapper` додає клас і контракт, але майже не приховує нової складності: клієнт усе ще має знати, як обробляти результат читання та помилки. Глибина модуля залежить від прихованої роботи відносно складності його інтерфейсу.

^aphsd-ch04-example-unix-vs-wrapper

## Пов'язані концепти

- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/modular-design-encapsulates-complexity|Модульний дизайн інкапсулює складність]]
- [[02-Concepts/deep-modules-hide-complexity|Глибокі модулі приховують складність]]
- [[01-Sources/books/a-philosophy-of-software-design/03-Concepts/abstractions-must-preserve-important-details|Абстракції мають зберігати важливі деталі]]
- [[02-Concepts/interface-segregation-avoids-dependencies-on-unused-operations|Розділення інтерфейсів усуває залежності від невикористовуваних операцій]]

## Пов'язані приклади коду

- Окремі code notes не створені: Unix I/O, garbage collection і Java streams у цьому розділі є порівняльними прикладами глибини API.

## Джерело та продовження

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-05-information-hiding-and-leakage|Розділ 5. Приховування інформації та її витік]]

- [[01-Sources/books/a-philosophy-of-software-design/A Philosophy of Software Design|Нотатка книги]]
- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-03-strategic-vs-tactical-programming|Розділ 3. Робочого коду недостатньо: стратегічне й тактичне програмування]]

## Пов'язані нотатки

- [[01-Sources/books/a-philosophy-of-software-design/02-Chapters/ch-02-nature-of-complexity|Розділ 2. Природа складності]]
