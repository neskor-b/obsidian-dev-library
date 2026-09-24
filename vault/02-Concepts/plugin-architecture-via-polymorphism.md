---
type: concept
scope: "shared-evergreen"
sources:
  - "clean-architecture"
title: "Поліморфізм дозволяє будувати plugin architecture"
aliases:
  - "Plugin architecture via polymorphism"
  - "Details as plugins"
tags:
  - source-note
  - concept
created: 2026-03-24
updated: 2026-09-24
source: "synthesis"
---

# Поліморфізм дозволяє будувати plugin architecture

## Визначення

`Plugin architecture` виникає тоді, коли стабільне ядро системи працює через контракт, а змінні деталі реалізують цей контракт як підключувані модулі. Поліморфізм робить таку побудову практичною: замість жорсткого знання про конкретний пристрій, `database` або `UI` ядро працює з абстракцією, а конкретна реалізація підставляється ззовні.

^plugin-architecture-via-polymorphism-definition

## Чому це важливо

Це перетворює "деталі" з того, що диктує форму всієї системи, на те, що можна замінювати без руйнування основних правил. Така архітектура зменшує coupling до технологій і дає команді свободу еволюціонувати інфраструктуру окремо від політик. Саме тому `UI` і сховище мають бути плагінами до бізнес-правил, а не їхнім центром тяжіння.

## Приклад

```typescript
interface PaymentGateway {
  charge(amountCents: number): Promise<void>;
}
class StripeGateway implements PaymentGateway {
  async charge(amountCents: number): Promise<void> { /* Stripe API */ }
}
class PaypalGateway implements PaymentGateway {
  async charge(amountCents: number): Promise<void> { /* PayPal API */ }
}
class CheckoutService {
  constructor(private readonly gateway: PaymentGateway) {}
  async completeOrder(amountCents: number): Promise<void> {
    await this.gateway.charge(amountCents);
  }
}

const checkout = new CheckoutService(new StripeGateway());
// У місці складання можна передати new PaypalGateway() без зміни CheckoutService.
```

`CheckoutService` залежить від `PaymentGateway`. Конкретну реалізацію передає код складання застосунку, тому заміна провайдера не вимагає правки в місці використання платежу. Новий адаптер має виконати той самий контракт і врахувати поведінку помилок та ідемпотентності.

^plugin-architecture-example

## Ознаки в коді

- Є стабільне ядро з контрактами, а конкретні адаптери підключаються на межі застосунку.
- Новий тип пристрою, сховища чи транспорту додається новою реалізацією, а не переписуванням основного сценарію.
- Компоненти можна збирати або розгортати окремо, бо їхній зв'язок проходить через явно визначені межі.

## Джерела

- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming#^clean-architecture-ch05-thesis-polymorphism-history]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming#^clean-architecture-ch05-thesis-plugins]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming#^clean-architecture-ch05-thesis-independent-components]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming#^clean-architecture-ch05-code-function-pointers]]

## Пов'язані концепти

- [[02-Concepts/dependency-inversion|Інверсія залежностей]]
- [[02-Concepts/open-closed-protects-high-level-policy|OCP захищає high-level policy через ієрархію залежностей]]
- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming|Розділ 5. Об'єктно-орієнтоване програмування]]

## Пов'язаний фрагмент

- [[01-Sources/books/clean-architecture/02-Chapters/ch-05-object-oriented-programming#^clean-architecture-ch05-code-function-pointers|Вказівники на функції в C як основа поліморфізму]]
