---
title: "Что такое дозакупка (restock)"
slug: restock
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Admin]
modules: [Inventory, Orders]
entities: [Inventory, Product, Order]
workflows: [WF-030]
related_screens: [SCR-120]
related_entities: [Inventory, Product, Order]
related_articles: [037-inventory-forecasting, 038-out-of-stock, 003-order, 025-marketplace-terms]
seo_title: "Что такое дозакупка (restock) на Amazon"
seo_description: "Что такое restock (дозакупка): своевременное пополнение запаса на Amazon по прогнозу продаж, чтобы избежать out of stock и лишних остатков."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (Recommended Ship In Quantity/Date, Days Of Supply, Рекомендация к дозакупке)
  - DOMAIN_MODEL.md (§4 Inventory, Order)
  - SCREEN_CATALOG.md (SCR-120)
  - WORKFLOW_CATALOG.md (WF-030)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое дозакупка (restock)

**Дозакупка** (restock) — своевременное пополнение запаса товара, чтобы не
допустить [дефицита (out of stock)](038-out-of-stock.md) и при этом не заморозить
лишний запас. Опирается на [прогноз запасов](037-inventory-forecasting.md).

## Кратко

Дозакупка отвечает на вопросы «сколько и когда заказать снова». Платформа
подсказывает это рекомендациями в инвентаре, а сам заказ создаётся из инвентаря.

## Что это такое

Restock — процесс пополнения: по прогнозу и рекомендациям продавец создаёт
[заказ](../foundations/003-order.md) на нужный объём к нужной дате.

## Ключевые ориентиры

Определения полей — в [справочнике](../../GLOSSARY.md):

- **Days of Supply** — на сколько хватит запаса.
- **Recommended Ship In Quantity / Date** — сколько и к какой дате отправить.
- **Рекомендация к дозакупке** — авто/ручная подсказка к пополнению.

## Зачем это нужно

- Избегать потери продаж из-за дефицита.
- Не замораживать деньги в избыточном запасе.
- Планировать закупку с учётом сроков изготовления и доставки.

## Как это делается

1. Смотрите прогноз и рекомендации в [инвентаре](../foundations/002-inventory.md)
   ([SCR-120](../../SCREEN_CATALOG.md)).
2. Отмечаете товары и создаёте заказ (**To order**) — сценарий **WF-030**.
3. Заказ уходит в обработку (см. [Что такое заказ](../foundations/003-order.md)).

## Термины и справочники

- Прогноз запасов: [Inventory Forecasting](037-inventory-forecasting.md).
- Дефицит: [Out of Stock](038-out-of-stock.md).
- Заказ: [Что такое заказ](../foundations/003-order.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Когда делать дозакупку? | Ориентируясь на days of supply и Recommended Ship In Date. |
| Сколько заказывать? | По рекомендации Recommended Ship In Quantity с учётом MOQ и сроков. |
| Как создать заказ на дозакупку? | Из инвентаря: выбрать товары → **To order** (WF-030). |

## Связанные статьи

- [Прогноз запасов](037-inventory-forecasting.md)
- [Out of Stock](038-out-of-stock.md)
- [003 — Заказ](../foundations/003-order.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон (`article_type: Marketplace Academy`, `series: Marketplace Terms`).
- [x] Показатели даны ссылкой на справочник, не дублируются.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
