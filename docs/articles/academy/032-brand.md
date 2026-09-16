---
title: "Что такое бренд"
slug: brand
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
entities: [Brand, Product, Category]
workflows: []
related_screens: [SCR-120]
related_entities: [Product, Category]
related_articles: [033-category, 001-product, 025-marketplace-terms]
seo_title: "Что такое бренд — торговая марка товара на Amazon"
seo_description: "Что такое бренд на Amazon: торговая марка товара, как он используется в Seller Exchange и чем отличается от процесса запуска бренда."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (поле Brand)
  - DOMAIN_MODEL.md (§4 Brand; DM17 Brand Launch)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое бренд

**Бренд** (Brand) — торговая марка, под которой продаётся товар на Amazon. В
Seller Exchange бренд — атрибут [товара](../foundations/001-product.md).

## Кратко

Бренд отвечает на вопрос «под какой маркой продаётся товар». Он используется в
каталоге и аналитике наравне с категорией.

## Что это такое

Бренд — атрибут товара, определяющий его торговую марку. Не путать с **запуском
бренда** (Brand Launch) — это отдельный процесс развития собственной марки на
Amazon; сам термин «бренд» здесь — про марку товара.

## Зачем это нужно

- Группирует товары одной марки.
- Влияет на восприятие и продвижение на Amazon.
- Используется в фильтрах и аналитике каталога.

## Где это видно в интерфейсе

Бренд отражён полем товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)).

## Связи с другими понятиями

- Бренд — **атрибут** товара; товар также относится к [категории](033-category.md).

Точные связи сущностей — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Термины и справочники

- Связанный термин: [Что такое категория](033-category.md).
- Каталог: [Термины маркетплейса](025-marketplace-terms.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Бренд и запуск бренда — одно и то же? | Нет. Бренд — марка товара; Brand Launch — отдельный процесс развития своей марки (DM17). |
| Где видно бренд? | В поле «Brand» у товара в инвентаре. |
| Бренд — это сущность? | На уровне термина — атрибут товара. |

## Связанные статьи

- [033 — Категория](033-category.md)
- [001 — Товар](../foundations/001-product.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон (`article_type: Marketplace Academy`, `series: Marketplace Terms`).
- [x] Разграничение Brand ↔ Brand Launch (DM17) отражено, не выдумано.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
