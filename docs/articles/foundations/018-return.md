---
title: "Что такое возврат"
slug: return
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client]
modules: [Inventory, Logistics]
entities: [Return, Product, Order]
workflows: []
related_screens: [SCR-120]
related_entities: [Product, Order]
related_articles: [001-product, 003-order]
seo_title: "Возврат в Seller Exchange — возврат товара"
seo_description: "Что такое возврат в Seller Exchange: возврат товара, как он связан с товаром и заказом и как возвраты влияют на показатели клиентского опыта."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Return)
  - ENTITY_RELATIONSHIPS.md (#78, #79, #89)
  - GLOSSARY.md (поле Returns; Voice of Customer)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: "confirmed (примечание: связь Return↔Order — Needs validation)"
---

> **Канонический источник (ru).** Переводы создаются из этого файла после
> отдельного решения. При правках сначала меняем источник.

# Что такое возврат

**Возврат** (Return) — возврат товара покупателем. Возвраты влияют на остатки и
на показатели клиентского опыта товара.

## Кратко

Возврат фиксирует, что товар вернули. Он связан с [товаром](001-product.md); число
возвратов отражается в инвентаре и учитывается в аналитике клиентского опыта.

## Что это такое

Возврат относится к товару. Детали возврата (в т.ч. замеры) открываются в
модалке деталей возврата. Возвраты также питают срез Voice of Customer
(показатели `concession_rate`, `badge_status`).

## Зачем это нужно

- Возвраты влияют на доступные остатки и здоровье запаса.
- Уровень возвратов — сигнал качества товара/листинга.
- Данные возвратов используются в аналитике клиентского опыта (NCX / Return Badge).

## Основные атрибуты

- **Товар** — какой товар возвращён.
- **Детали возврата** — причина, замеры (модалка деталей возврата).

## Жизненный цикл и статусы

Отдельного набора статус-кодов у возврата в базе знаний нет.

## Связи с другими сущностями

- Возврат **ссылается** на товар.
- Связь возврата с заказом в документации не описана — **Needs validation**.
- Показатели возвратов используются в срезе Voice of Customer.

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

С возвратами работает **Client** — видит возвраты по своим товарам. Доступ — см.
[Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Инвентарь — товары | Поле возвратов по товару |

Детали возврата открываются в модалке `ReturnDetailsModal` (замеры —
`MeasureModal`).

## Связанные сценарии

Отдельного сценария в каталоге нет — возвраты сопровождают работу с товаром и
складом.

## Термины и справочники

- Термины: поле «Returns», Voice of Customer — [GLOSSARY](../../GLOSSARY.md).
- Связи: [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| На что влияет возврат? | На доступные остатки и на показатели клиентского опыта (NCX / Return Badge). |
| Связан ли возврат с заказом? | В документации связь Return↔Order пока не описана (*Needs validation*). |
| Где видно возвраты? | В инвентаре (поле возвратов) и в срезе Voice of Customer. |

## Связанные статьи

- [001 — Товар](001-product.md)
- [003 — Заказ](003-order.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Неопределённость помечена: связь Return↔Order — *Needs validation*.
- [x] Не выдуманы статусы возврата (их нет в КБ).
- [x] Внутренние ссылки корректны.
