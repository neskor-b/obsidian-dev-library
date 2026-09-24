---
type: playbook
scope: playbook
title: "Як підходити до задачі system design"
aliases:
  - "Approach a system design problem"
  - "7-step system design framework"
sources:
  - "system-design-handbook-system-design"
tags:
  - playbook
created: 2026-03-25
updated: 2026-03-25
source: "system-design-handbook-guide"
---

# Як підходити до задачі system design

## Коли використовувати

Цей playbook підходить для відкритих задач на кшталт interview prompt, design review або ранньої архітектурної сесії, коли потрібно швидко перейти від нечіткої проблеми до аргументованого high-level design.

## Кроки

1. Уточни вимоги: відокрем функціональні вимоги від нефункціональних, з'ясуй scale, read/write profile, latency target, consistency needs, retention і failure expectations. ^sdh-playbook-step-1
2. Проведи межі системи: визнач, що входить у задачу, які є зовнішні залежності, і зафіксуй API або головні точки взаємодії. ^sdh-playbook-step-2
3. Намалюй high-level architecture: покажи клієнтів, load balancer, application layer, storage, cache, queue і happy path руху даних. ^sdh-playbook-step-3
4. Змоделюй дані й storage: виріши, які сутності, індекси й тип сховища потрібні, і чи допустимі реплікація, eventual consistency або географічний розподіл. ^sdh-playbook-step-4
5. Продумай scalability та reliability: додай кешування, шардінг, реплікацію, failover, backpressure або асинхронну обробку там, де цього вимагає навантаження. ^sdh-playbook-step-5
6. Озвуч trade-offs явно: поясни, чому обрав саме ці компоненти, що отримуєш натомість і за яких умов змінив би підхід. ^sdh-playbook-step-6
7. Заверши валідацією: перевір security, observability, maintainability, bottlenecks і те, чи справді дизайн закриває вимоги end-to-end. ^sdh-playbook-step-7

## Орієнтовний таймбокс для інтерв'ю

- 5 хвилин на уточнення вимог
- 10 хвилин на high-level design
- 15 хвилин на занурення в 1-2 критичні компоненти
- 10 хвилин на scalability, failure handling і trade-offs
- 5 хвилин на підсумок і перевірку рішення

## Сигнали успіху

- Ти можеш пояснити кожен компонент через конкретну вимогу або обмеження.
- У дизайні явно проговорені bottlenecks, failure modes і ключові метрики для спостереження.
- Рішення виглядає достатньо простим для поточного масштабу, але має зрозумілий шлях еволюції.

## Типові помилки

- Стрибати одразу до мікросервісів, API або вибору БД, не зафіксувавши вимоги.
- Вибирати SQL, NoSQL, cache чи queue як шаблон "за замовчуванням", а не як відповідь на конкретне навантаження.
- Не проговорювати security, observability, consistency model і failure handling.

## Пов'язані концепти

- [[01-Sources/articles/system-design-handbook-system-design/02-Notes/system-design-starts-with-requirements-and-trade-offs|System design починається з вимог і trade-offs]]
- [[02-Concepts/architecture-governs-cost-of-change|Архітектура визначає вартість змін]]

## Джерела

- [[01-Sources/articles/system-design-handbook-system-design/02-Notes/system-design-starts-with-requirements-and-trade-offs#^sdh-system-design-main-idea]]
- [[01-Sources/articles/system-design-handbook-system-design/02-Notes/system-design-starts-with-requirements-and-trade-offs#^sdh-system-design-thesis-requirements]]
- [[01-Sources/articles/system-design-handbook-system-design/02-Notes/system-design-starts-with-requirements-and-trade-offs#^sdh-system-design-thesis-tradeoffs]]

