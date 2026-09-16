---
title: "Что такое out of stock"
slug: out-of-stock
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Admin]
modules: [Inventory]
entities: [Inventory, Product]
workflows: []
related_screens: [SCR-120]
related_entities: [Inventory, Product, Order]
related_articles: [037-inventory-forecasting, 002-inventory, 025-marketplace-terms]
seo_title: "Что такое out of stock — дефицит товара на Amazon"
seo_description: "Что такое out of stock: ситуация, когда товар закончился на складе, почему это вредно для продавца и как её предотвратить."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (Available, Days Of Supply, No Sale Last 6 Months, Fba Minimum Inventory Level)
  - DOMAIN_MODEL.md (§4 Inventory)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое out of stock

**Out of stock** — ситуация, когда товар закончился на складе и недоступен к
продаже. Для продавца это потеря продаж и позиций в выдаче, поэтому дефицит
стараются предотвращать.

## Кратко

Out of stock — «нулевой остаток»: продавать нечего. Признаки приближающегося
дефицита видны в инвентаре по остаткам и прогнозу запаса.

## Почему это вредно

- Потерянные продажи, пока товара нет.
- Просадка позиций и видимости товара на Amazon.
- Дополнительные сборы Amazon за низкий уровень запаса.

## Как это увидеть заранее

Смотрите показатели в [инвентаре](../foundations/002-inventory.md)
(определения — в [справочнике](../../GLOSSARY.md)):

- **Available** — доступный остаток.
- **Days of Supply** — на сколько дней хватит запаса
  (см. [Прогноз запасов](037-inventory-forecasting.md)).
- **Fba Minimum Inventory Level** — минимальный уровень, ниже которого риск stock-out.
- **No Sale Last 6 Months** — товары без продаж (обратная ситуация — залежавшийся запас).

## Как предотвратить

- Следить за days of supply и рекомендациями по пополнению.
- Планировать дозакупку заранее (см. [Restock — планируется, ART-039]).

## Где это видно в интерфейсе

Остатки и показатели риска — колонки [инвентаря](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)).

## Термины и справочники

- Прогноз запасов: [Inventory Forecasting](037-inventory-forecasting.md).
- Инвентарь: [Что такое инвентарь](../foundations/002-inventory.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Чем вреден out of stock? | Потерянные продажи, просадка позиций, сборы за низкий запас. |
| Как заметить дефицит заранее? | По Available, Days of Supply и Fba Minimum Inventory Level. |
| Как избежать? | Планировать дозакупку по прогнозу запасов (Restock — ART-039). |

## Связанные статьи

- [Прогноз запасов](037-inventory-forecasting.md)
- [002 — Инвентарь](../foundations/002-inventory.md)
- [Термины маркетплейса](025-marketplace-terms.md)
- Restock (дозакупка) — планируется (ART-039)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Показатели даны ссылкой на справочник, не дублируются.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
