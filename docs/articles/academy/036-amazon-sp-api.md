---
title: "Что такое Amazon SP-API"
slug: amazon-sp-api
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Admin]
modules: [Integrations, Inventory]
entities: [Integration, Store, Product]
workflows: [WF-034]
related_screens: [SCR-280]
related_entities: [Store, Report, Inventory]
related_articles: [006-store, 025-marketplace-terms]
seo_title: "Что такое Amazon SP-API — интеграция с данными Amazon"
seo_description: "Что такое Amazon SP-API: программный интерфейс Amazon для доступа к данным продавца, через который Seller Exchange получает товары, продажи и отчёты."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Integration)
  - ENTITY_RELATIONSHIPS.md (#105)
  - "docs/Data filters*.md (integrations/*)"
  - SCREEN_CATALOG.md (SCR-280)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Что такое Amazon SP-API

**Amazon SP-API** (Selling Partner API) — программный интерфейс Amazon для доступа
к данным продавца. Через него Seller Exchange получает данные о товарах, продажах
и отчётах и обновляет их автоматически.

## Кратко

SP-API — «канал» между Amazon и платформой. Подключив
[магазин](../foundations/006-store.md), вы даёте платформе доступ к данным Amazon
через SP-API, и они начинают синхронизироваться.

## Что это такое

SP-API — одна из **интеграций** платформы (наряду с SellerBoard). Это источник
внешних данных, привязанный к магазину; отдельной пользовательской «сущности» у
него нет — это способ получения данных.

## Зачем это нужно

- Автоматическая синхронизация товаров и продаж из Amazon.
- Питает инвентарь, отчёты и аналитику актуальными данными.
- Убирает ручной ввод данных Amazon.

## Где это видно в интерфейсе

Интеграция подключается вместе с [магазином](../foundations/006-store.md)
([SCR-280](../../SCREEN_CATALOG.md)); данные затем видны в инвентаре и отчётах.

## Связи с другими понятиями

- Интеграция (SP-API) **подключается к** магазину и питает инвентарь/отчёты.

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md) (#105).

> **Connected App / «магазин приложений»** — функционал в разработке
> (*Needs validation*, DM6). Сейчас модель внешних данных — только интеграции
> (Amazon SP-API, SellerBoard).

## Термины и справочники

- Магазин: [Что такое магазин](../foundations/006-store.md).
- Каталог терминов: [Термины маркетплейса](025-marketplace-terms.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Что даёт SP-API? | Доступ к данным продавца на Amazon (товары, продажи, отчёты). |
| Нужно ли подключать вручную? | Подключение идёт через магазин ([SCR-280](../../SCREEN_CATALOG.md)). |
| Есть ли магазин приложений? | Пока нет — Connected App в разработке (DM6). |

## Связанные статьи

- [006 — Магазин](../foundations/006-store.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] SP-API описан как интеграция; Connected App помечен *Needs validation* (DM6).
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
