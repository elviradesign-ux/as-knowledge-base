---
title: "ASIN vs SKU vs FNSKU"
slug: asin-vs-sku-vs-fnsku
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Researcher, Supervisor, Admin]
modules: [Product, Inventory]
entities: [ASIN, SKU, FNSKU, Product, Barcode]
workflows: []
related_screens: [SCR-120]
related_entities: [Product, ASIN, FNSKU, Barcode]
related_articles: [026-asin, 027-sku, 025-marketplace-terms]
seo_title: "ASIN vs SKU vs FNSKU — в чём разница"
seo_description: "ASIN vs SKU vs FNSKU: чем различаются идентификаторы товара на Amazon — кто их задаёт, для чего они нужны и как соотносятся в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (ASIN, Fnsku, Баркод)
  - DOMAIN_MODEL.md (§4 ASIN, SKU — атрибут DM13, FNSKU, Barcode)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# ASIN vs SKU vs FNSKU

Три идентификатора часто путают. Коротко: **ASIN** задаёт Amazon для листинга,
**SKU** задаёт продавец для своего учёта, **FNSKU** — код Amazon для отслеживания
товара на складах FBA.

## Кратко

- **ASIN** — «имя» товара на Amazon (общее для листинга).
- **SKU** — ваш собственный артикул (атрибут товара).
- **FNSKU** — код Amazon для конкретной единицы на складе FBA.

## Сравнение

| Идентификатор | Кто задаёт | Для чего | Область |
|---|---|---|---|
| **ASIN** | Amazon | Идентификация товара в каталоге/листинге | Публичный, на Amazon |
| **SKU** | Продавец | Внутренний учёт позиций продавца | Учёт продавца (атрибут) |
| **FNSKU** | Amazon | Отслеживание единицы товара на складах FBA | Склад FBA |

## Как они соотносятся

- Один **ASIN** = товар в каталоге. Продавец сопоставляет ему свой **SKU**.
- Для хранения на FBA товар получает **FNSKU**.
- Штрихкод на упаковке (UPC/EAN или FNSKU) — см.
  [Barcode / UPC / EAN](035-barcode-upc-ean.md).

## Зачем это нужно

- Понимание разницы снижает путаницу при работе с инвентарём и отправками.
- SKU нужен для собственного учёта; ASIN — для действий на Amazon; FNSKU — для склада.

## Где это видно в интерфейсе

Все три идентификатора встречаются как поля товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)); определения — в
[справочнике полей](../../GLOSSARY.md).

## Термины и справочники

- Отдельные статьи: [ASIN](026-asin.md), [SKU](027-sku.md).
- Штрихкоды: [Barcode / UPC / EAN](035-barcode-upc-ean.md).
- Идентификаторы товара: [Термины маркетплейса](025-marketplace-terms.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Что из этого задаёт продавец? | Только SKU. ASIN и FNSKU задаёт Amazon. |
| FNSKU и баркод — одно и то же? | FNSKU может выступать штрихкодом на складе FBA; см. статью Barcode / UPC / EAN. |
| Является ли SKU отдельной сущностью? | Нет, это атрибут товара (DM13). |

## Связанные статьи

- [Что такое ASIN](026-asin.md)
- [Что такое SKU](027-sku.md)
- [Barcode / UPC / EAN](035-barcode-upc-ean.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон (`article_type: Marketplace Academy`, `series: Marketplace Terms`).
- [x] Source documents — перечислены и актуальны.
- [x] SKU описан как атрибут (DM13); идентификаторы не выдуманы.
- [x] Нет дублирования — ссылки на отдельные статьи ASIN/SKU/Barcode.
- [x] Внутренние ссылки корректны (academy↔foundations).
