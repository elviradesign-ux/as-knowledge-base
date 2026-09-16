---
title: "Что такое вариация"
slug: variation
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Researcher, Buyer, Admin]
modules: [Product, Inventory]
entities: [Variation, Product, ASIN]
workflows: []
related_screens: [SCR-120, SCR-124]
related_entities: [Product, ASIN, Product Card]
related_articles: [001-product, 013-product-card, 025-marketplace-terms]
seo_title: "Что такое вариация — вариант товара на Amazon"
seo_description: "Что такое вариация товара на Amazon: вариант (цвет, размер) как отдельный товар и родительский товар, выражающий связь между позициями."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (поле «Вариация»)
  - DOMAIN_MODEL.md (§4 Parent Product / Variation; DM18)
  - ENTITY_RELATIONSHIPS.md (#8, #9)
  - SCREEN_CATALOG.md (SCR-120, SCR-124)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое вариация

**Вариация** (Variation) — вариант товара (например, другой цвет или размер). В
Seller Exchange вариация — это тоже [товар](../foundations/001-product.md);
**родительский товар (Parent Product)** выражает связь и зависимость между
позициями (подтверждено, DM18).

## Кратко

Вариации — это связанные варианты одной товарной линейки. Каждая вариация — свой
товар со своим ASIN; родительский товар объединяет их.

## Что это такое

- **Вариация** — отдельный товар (свой ASIN), вариант другого.
- **Родительский товар (Parent Product)** — указывает связь и зависимость между
  вариациями.

## Зачем это нужно

- Группирует связанные варианты (цвет/размер/упаковка).
- Помогает вести учёт линейки товаров вместе.
- Отражает зависимости между позициями каталога.

## Где это видно в интерфейсе

Признак вариации — поле товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)); работа с вариациями и привязкой — в
[карточке товара](../foundations/013-product-card.md)
([SCR-124](../../SCREEN_CATALOG.md)) и модалке `BindProductModal`.

## Связи с другими понятиями

- Вариация **это** товар; **принадлежит** родительскому товару.

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md) (#8, #9).

## Термины и справочники

- Товар: [Что такое товар](../foundations/001-product.md).
- Карточка товара: [Что такое карточка товара](../foundations/013-product-card.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Вариация — это отдельный товар? | Да, вариация — это товар со своим ASIN (DM18). |
| Что делает родительский товар? | Выражает связь и зависимость между вариациями. |
| Где привязать вариацию? | В карточке товара / модалке `BindProductModal`. |

## Связанные статьи

- [001 — Товар](../foundations/001-product.md)
- [013 — Карточка товара](../foundations/013-product-card.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Variation = Product; Parent = связь (DM18) — отражено, не выдумано.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
