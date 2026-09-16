---
title: "Подключить магазин Amazon"
slug: connect-amazon-store
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client]
roles: [Client]
modules: [Stores, Integrations]
entities: [Store, Integration, Product]
workflows: [WF-034]
related_screens: [SCR-280, SCR-281]
related_entities: [Store, Integration]
related_articles: [046-first-login, 049-create-first-product, 006-store, 036-amazon-sp-api]
seo_title: "Как подключить магазин Amazon в Seller Exchange"
seo_description: "Как подключить магазин Amazon Seller Central в Seller Exchange, чтобы данные о товарах и продажах синхронизировались автоматически."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-280, SCR-281)
  - WORKFLOW_CATALOG.md (WF-034)
  - articles/foundations/006-store.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие магазина — в
> [Что такое магазин](../foundations/006-store.md).

# Подключить магазин Amazon

## Кратко

Подключение [магазина](../foundations/006-store.md) даёт платформе доступ к данным
Amazon через [SP-API](../academy/036-amazon-sp-api.md); после этого товары и
продажи синхронизируются автоматически. Без магазина инвентарь пуст.

## Предварительные условия

- Роль Client; выполнен [первый вход](046-first-login.md).
- Есть аккаунт Amazon Seller Central.

## Шаги

1. Откройте **Мои магазины** ([SCR-280](../../SCREEN_CATALOG.md)).
2. Добавьте магазин (`ShopModal`).
3. Авторизуйте доступ через Amazon SP-API.
4. Дождитесь синхронизации данных.

## Результат

- Магазин подключён; товары и продажи подтягиваются в
  [инвентарь](051-use-inventory.md) и отчёты
  ([SCR-281](../../SCREEN_CATALOG.md) — отчёты парсинга).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Данные не появились | Синхронизация не завершена/нет авторизации | Проверить авторизацию SP-API |
| Саб-юзер не видит магазин | Ограничение по `shopIds` | Настроить доступ ([права](054-manage-users-and-permissions.md)) |

## Связанные материалы

- Далее: [Создать первый товар](049-create-first-product.md)
- Понятия: [Магазин](../foundations/006-store.md), [Amazon SP-API](../academy/036-amazon-sp-api.md)

## Чеклист ревью

- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-034).
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
