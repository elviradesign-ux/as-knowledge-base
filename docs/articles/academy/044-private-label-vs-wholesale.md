---
title: "Private Label vs Wholesale"
slug: private-label-vs-wholesale
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Researcher, Admin]
modules: [Product Research, Product]
entities: [Strategy, Product]
workflows: []
related_screens: [SCR-120]
related_entities: [Strategy, Product, Supplier]
related_articles: [011-supplier, 001-product, 025-marketplace-terms]
seo_title: "Private Label vs Wholesale — стратегии продаж на Amazon"
seo_description: "Private Label vs Wholesale: две стратегии сорсинга на Amazon — собственная марка против оптовой перепродажи, и как они отражены в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - ENTITY_STATES.md (Стратегия сорсинга)
  - GLOSSARY.md (поле «Стратегия»)
  - DOMAIN_MODEL.md (§4 Strategy)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Private Label vs Wholesale

**Private Label** и **Wholesale** — две стратегии сорсинга (закупки) товара на
Amazon. В Seller Exchange стратегия — это атрибут товара (поле «Стратегия»); её
значения перечислены в [Entity States](../../ENTITY_STATES.md).

## Кратко

- **Private Label** — продажа товара под **собственной маркой**.
- **Wholesale** — **оптовая перепродажа** товаров известных брендов.

## В чём разница

| | Private Label | Wholesale |
|---|---|---|
| Марка | Своя (собственный бренд) | Чужая (известный бренд) |
| Суть | Создаёте и развиваете свой листинг | Перепродаёте оптом закупленный товар |
| Пример поля стратегии | `PRIVATE_LABEL` | `WHOLESALE_USA` |

Другие стратегии сорсинга (например, `DROPSHIPPING`, `ONLINE_ARBITRAGE_CHINA`) —
в [Entity States → Стратегия сорсинга](../../ENTITY_STATES.md).

## Зачем это нужно

- Стратегия определяет подход к закупке и развитию товара.
- Влияет на маржинальность, конкуренцию и работу с поставщиком.
- Помогает сегментировать каталог по способу заработка.

## Где это видно в интерфейсе

Стратегия отражена полем «Стратегия» у товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)).

## Термины и справочники

- Значения стратегий: [Entity States](../../ENTITY_STATES.md).
- Поставщик: [Что такое поставщик](../foundations/011-supplier.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| В чём главное отличие? | Private Label — своя марка; Wholesale — перепродажа чужих брендов оптом. |
| Есть ли другие стратегии? | Да — DROPSHIPPING, ONLINE_ARBITRAGE_CHINA и др. (Entity States). |
| Где задаётся стратегия? | В поле «Стратегия» у товара. |

## Связанные статьи

- [011 — Поставщик](../foundations/011-supplier.md)
- [001 — Товар](../foundations/001-product.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md) и [ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Значения стратегий даны ссылкой на Entity States, не выдуманы.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
