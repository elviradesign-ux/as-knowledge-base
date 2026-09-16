---
title: "Что такое ASIN"
slug: asin
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Researcher, Supervisor, Admin]
modules: [Product, Inventory, Supervisor Settings]
entities: [ASIN, Product, FNSKU, Barcode]
workflows: []
related_screens: [SCR-120, SCR-320]
related_entities: [Product, Product Card, FNSKU, Barcode]
related_articles: [001-product, 013-product-card, 025-marketplace-terms]
seo_title: "Что такое ASIN — идентификатор товара на Amazon"
seo_description: "Что такое ASIN (Amazon Standard Identification Number): идентификатор товара на Amazon, чем отличается от SKU и FNSKU и как используется в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (ASIN)
  - DOMAIN_MODEL.md (§4 ASIN, Product)
  - ENTITY_RELATIONSHIPS.md (#1)
  - SCREEN_CATALOG.md (SCR-120, SCR-320)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое ASIN

**ASIN** (Amazon Standard Identification Number) — уникальный идентификатор товара
на Amazon. Это «имя» позиции на маркетплейсе, по которому товар находят и которым
управляют.

## Кратко

ASIN однозначно называет товар на Amazon. В Seller Exchange именно вокруг ASIN
собираются данные о [товаре](../foundations/001-product.md): остатки, продажи,
себестоимость и данные поставщика.

## Что это такое

ASIN — идентификатор Amazon, привязанный к товару. Он проверяется ASIN-чекером и
используется во всех разделах, где встречается товар.

## Чем ASIN отличается от SKU и FNSKU

- **ASIN** — идентификатор товара на самом Amazon (общий для листинга).
- **SKU** — артикул продавца; это **атрибут** товара, а не отдельная сущность.
- **FNSKU** — внутренний код Amazon для отслеживания товара на складах FBA.

Подробное сравнение будет в отдельной статье _ASIN vs SKU vs FNSKU (планируется,
ART-028)_.

## Зачем это нужно

- ASIN — ключ товара: по нему сводятся все данные и аналитика.
- Корректный ASIN обеспечивает точность инвентаря, заказов и отчётов.
- Массовые операции (добавление/удаление списка ASIN) ускоряют работу с каталогом.

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Инвентарь — товары | ASIN как идентификатор строки товара |
| [SCR-320](../../SCREEN_CATALOG.md) Настройки — ASIN-чекер | Проверка ASIN (Supervisor) |

## Связи с другими понятиями

- Товар **имеет** ASIN.
- ASIN связан с [карточкой товара](../foundations/013-product-card.md), FNSKU и
  баркодом.

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Термины и справочники

- Термин: [ASIN](../../GLOSSARY.md).
- Идентификаторы товара: см. [Термины маркетплейса](025-marketplace-terms.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| ASIN и SKU — это одно и то же? | Нет. ASIN — идентификатор Amazon; SKU — артикул продавца (атрибут товара). |
| Где проверяется ASIN? | В ASIN-чекере ([SCR-320](../../SCREEN_CATALOG.md), Supervisor). |
| Можно ли работать со списком ASIN сразу? | Да, поддерживаются массовые операции со списком ASIN. |

## Связанные статьи

- [001 — Товар](../foundations/001-product.md)
- [013 — Карточка товара](../foundations/013-product-card.md)
- [Термины маркетплейса](025-marketplace-terms.md)
- ASIN vs SKU vs FNSKU — планируется (ART-028)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон (`article_type: Marketplace Academy`, `series: Marketplace Terms`).
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования — сравнение ASIN/SKU/FNSKU кратко, полное — в ART-028 (планируется).
- [x] Экраны подтверждены (SCR-120, SCR-320).
- [x] Внутренние ссылки корректны (в т.ч. кросс-папка academy↔foundations).
