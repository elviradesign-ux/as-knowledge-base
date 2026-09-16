---
title: "Что такое прогноз запасов"
slug: inventory-forecasting
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Admin]
modules: [Inventory, Analytics]
entities: [Inventory, Product]
workflows: []
related_screens: [SCR-120]
related_entities: [Inventory, Product, Order]
related_articles: [002-inventory, 038-out-of-stock, 025-marketplace-terms]
seo_title: "Прогноз запасов на Amazon — days of supply и планирование дозакупки"
seo_description: "Что такое прогноз запасов: как показатели days of supply и weeks of cover помогают спланировать дозакупку и не допустить out of stock."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (Days Of Supply, Weeks Of Cover, Recommended Ship In*)
  - DOMAIN_MODEL.md (§4 Inventory)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое прогноз запасов

**Прогноз запасов** (Inventory Forecasting) — оценка того, на сколько хватит
текущего запаса и когда нужно пополнить склад. Он помогает планировать закупку и
избегать [дефицита (out of stock)](038-out-of-stock.md).

## Кратко

Прогноз отвечает на вопрос «когда закончится товар и когда заказывать снова». Он
строится на скорости продаж и текущих остатках и выражается набором показателей в
инвентаре.

## Ключевые показатели

Определения полей — в [справочнике полей инвентаря](../../GLOSSARY.md):

- **Days of Supply** — на сколько дней хватит запаса.
- **Historical Days of Supply** — тот же показатель по прошлым периодам (тренд).
- **Weeks of Cover (T30 / T90)** — на сколько недель хватит по продажам за 30/90 дней.
- **Recommended Ship In Quantity / Date** — сколько и к какой дате рекомендуется
  отправить на склад.

## Зачем это нужно

- Планировать дозакупку заранее.
- Не допускать дефицита и не замораживать лишний запас.
- Опираться на рекомендации Amazon по пополнению.

## Где это видно в интерфейсе

Показатели прогноза — колонки [инвентаря](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)), группы «Прогноз запаса» и «Рекомендации».

## Термины и справочники

- Инвентарь: [Что такое инвентарь](../foundations/002-inventory.md).
- Дефицит: [Out of Stock](038-out-of-stock.md).
- Поля: [GLOSSARY](../../GLOSSARY.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Что такое Days of Supply? | Прогноз, на сколько дней хватит текущего запаса. |
| Как понять, когда заказывать? | По рекомендациям Recommended Ship In Quantity/Date и days of supply. |
| Чем это помогает? | Планировать дозакупку и избегать out of stock. |

## Связанные статьи

- [002 — Инвентарь](../foundations/002-inventory.md)
- [Out of Stock](038-out-of-stock.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Показатели даны ссылкой на справочник полей, не дублируются.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
