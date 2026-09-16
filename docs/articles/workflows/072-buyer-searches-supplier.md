---
title: "Байер ищет поставщика"
slug: buyer-searches-supplier
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Buyer]
roles: [Buyer]
modules: [Suppliers, Product Research]
entities: [Supplier, Supplier Card, Product, Product Card]
workflows: [WF-003, WF-020]
related_screens: [SCR-190, SCR-191, SCR-192]
related_entities: [Supplier, Supplier Card, Product]
related_articles: [071-supervisor-checks-product-card, 011-supplier, 012-supplier-card]
seo_title: "Как байеру найти поставщика — Seller Exchange"
seo_description: "Пошаговый сценарий: как байер ищет поставщика по запросу супервайзера или клиента, заполняет карточку поставщика и возвращает на проверку."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-003, WF-020)
  - SCREEN_CATALOG.md (SCR-190, SCR-191, SCR-192)
  - ENTITY_STATES.md (Статусы товара; статус карточки поставщика)
  - articles/foundations/011-supplier.md, 012-supplier-card.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Продолжение
> [проверки супервайзером](071-supervisor-checks-product-card.md). Понятия — в
> [Поставщик](../foundations/011-supplier.md) и
> [Карточка поставщика](../foundations/012-supplier-card.md).

# Байер ищет поставщика

## Кратко

Сценарий описывает, как **Buyer** находит поставщика под товар по запросу
супервайзера или клиента, заполняет карточку поставщика и возвращает её на
верификацию. Сценарий: **WF-003** (верификация супервайзером — **WF-020**).

## Кому и когда пригодится

- **Buyer** — когда товар отправлен на поиск поставщика.

## Предварительные условия

- Роль Buyer; есть запросы на поиск (от супервайзера или клиента).

## Шаги

1. Откройте **Поиск поставщиков — от супервайзера**
   ([SCR-191](../../SCREEN_CATALOG.md)) или **от клиента**
   ([SCR-192](../../SCREEN_CATALOG.md)).
2. Возьмите товар в работу — статус `BUYER_PICKED_PRODUCT`.
3. Найдите поставщика; заполните
   [карточку поставщика](../foundations/012-supplier-card.md) (`SupplierCardModal`,
   `AddSupplierModal`).
4. Зафиксируйте результат:
   - поставщик найден — `BUYER_FOUND_SUPPLIER`;
   - не найден — `SUPPLIER_WAS_NOT_FOUND_BY_BUYER`;
   - цена не подходит — `SUPPLIER_PRICE_WAS_NOT_ACCEPTABLE`.
5. Верните карточку супервайзеру на верификацию (**WF-020**).

Коды статусов — [Entity States](../../ENTITY_STATES.md) (ветка «от клиента» —
`FROM_CLIENT_*`).

## Результат

- Карточка поставщика заполнена и отправлена на верификацию.
- При успехе супервайзер публикует товар на биржу (`COMPLETE_SUCCESS`).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет запросов на поиск | Товары не отправлены супервайзером | Дождаться `TO_BUYER_FOR_RESEARCH` |
| Цена не подходит | Условия поставщика | Зафиксировать `SUPPLIER_PRICE_WAS_NOT_ACCEPTABLE` |

## Связанные материалы

- Предыдущий шаг: [Супервайзер проверяет карточку](071-supervisor-checks-product-card.md)
- Концепт: [Поставщик](../foundations/011-supplier.md), [Карточка поставщика](../foundations/012-supplier-card.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-003/020).
- [x] Статусы дословно из ENTITY_STATES.
- [ ] Ревью вторым человеком.
