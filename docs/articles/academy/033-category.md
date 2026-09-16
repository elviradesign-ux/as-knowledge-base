---
title: "Что такое категория"
slug: category
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Researcher, Admin]
modules: [Product, Inventory]
entities: [Category, Product, Brand]
workflows: []
related_screens: [SCR-120]
related_entities: [Product, Brand]
related_articles: [032-brand, 001-product, 025-marketplace-terms]
seo_title: "Что такое категория — раздел каталога Amazon"
seo_description: "Что такое категория на Amazon: раздел каталога, к которому относится товар, а также подкатегория и ранги, и как это используется в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (поля Category / Subcategory / Category Rank)
  - DOMAIN_MODEL.md (§4 Category)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое категория

**Категория** (Category) — раздел каталога Amazon, к которому относится товар.
У товара также есть **подкатегория** и позиции в рангах категории/подкатегории.

## Кратко

Категория определяет, в каком разделе каталога находится товар (например,
Electronics, Clothing). Подкатегория уточняет место внутри категории.

## Что это такое

Категория — атрибут товара. С ней связаны показатели: ранг в категории
(Category Rank) и подкатегории (Subcategory Rank), а также ссылки на страницы
категории на Amazon.

## Зачем это нужно

- Определяет место товара в каталоге Amazon.
- Ранги категории/подкатегории показывают популярность товара.
- Используется в фильтрах и аналитике.

## Где это видно в интерфейсе

Категория, подкатегория и их ранги — поля товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)). Управление категориями на стороне
платформы — модалка `CategoryModal` (Админ → Настройки).

## Связи с другими понятиями

- Категория — **атрибут** товара; товар также относится к [бренду](032-brand.md).

Точные связи сущностей — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Термины и справочники

- Связанный термин: [Что такое бренд](032-brand.md).
- Поля каталога: [GLOSSARY](../../GLOSSARY.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Чем категория отличается от подкатегории? | Подкатегория уточняет место товара внутри категории. |
| Что такое Category Rank? | Позиция товара внутри категории (меньше — популярнее). |
| Где видно категорию? | В полях товара в инвентаре. |

## Связанные статьи

- [032 — Бренд](032-brand.md)
- [001 — Товар](../foundations/001-product.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Source documents — перечислены и актуальны.
- [x] Иерархия категорий Amazon не выдумывается сверх подтверждённых полей.
- [x] Внутренние ссылки корректны (academy↔foundations).
