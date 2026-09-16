---
title: "Уведомления"
slug: notifications
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Storekeeper, Freelancer, Admin]
roles: [Client, Buyer, Storekeeper, Freelancer, Admin]
modules: [Notifications]
entities: [Notification, Order, Box, Tariff, Service Request]
workflows: []
related_screens: [SCR-013]
related_entities: [Notification, Order, Box, Tariff]
related_articles: [019-notification, orders-list, warehouse-in-stock]
seo_title: "Уведомления: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану уведомлений в Seller Exchange: вкладки по заказам, коробкам, тарифам коробок, заявкам и общие уведомления."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-013)
  - reference/routes-by-role.md (вкладки уведомлений)
  - figma-mcp/sources/mhtml/ (захваты)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятие уведомления — в
> [Что такое уведомление](../foundations/019-notification.md). Визуальные
> источники — mhtml.

# Уведомления

## Кратко

Экран уведомлений сообщает о событиях платформы и разбит на вкладки по темам.
Route: `/notifications` (`GeneralNotificationsView` / `CategoryRootView`,
[SCR-013](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Client, Buyer, Storekeeper, Freelancer, Admin** — следить за событиями по
  своим объектам.

## Предварительные условия

- Доступ к разделу (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).

## Элементы экрана

Уведомления сгруппированы по вкладкам (у Client — пять; роуты — из
[reference/routes-by-role.md](../../reference/routes-by-role.md)):

- **По заказам** (`/notifications/on-orders`).
- **По коробкам** (`/notifications/on-boxes`).
- **По тарифам коробок** (`/notifications/on-boxes-tariffs`).
- **Сообщения по запросам** (`/notifications/request-messages`).
- **Общие** (`/notifications/general`).

Каждое уведомление ссылается на объект (заказ, коробку, тариф, заявку).

## Действия

- Открыть уведомление → перейти к связанному объекту
  ([заказ](orders-list.md), [коробка](warehouse-in-stock.md), тариф, заявка).
- Разобрать/отметить уведомление в соответствующей вкладке.

## Результат

- Пользователь в курсе событий и переходит к объекту, требующему действия.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [orders-list](orders-list.md) Список заказов | Объекты «по заказам» |
| [warehouse-in-stock](warehouse-in-stock.md) Коробки на складе | Объекты «по коробкам» |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Client-Notifications-Orders.*.mhtml` (light/dark, En/Uk) — по заказам.
- `Client-Notifications-Boxes.Dark.En.mhtml` — по коробкам _(Dark/En)_.
- `Client-Notifications-OnBoxesTariffs.Dark.En.mhtml` — по тарифам коробок _(Dark/En)_.
- `Client-Notifications-Requests.Dark.En.mhtml` — по запросам _(Dark/En)_.
- `Client-Notifications-General.Dark.En.mhtml` — общие _(Dark/En)_.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не вижу нужную вкладку | Роль/набор вкладок отличается | У Client — 5 вкладок; у других — иной набор |
| Уведомление не открывает объект | Объект удалён/нет доступа | Проверить объект и права |

## Связанные материалы

- Концепт: [Что такое уведомление](../foundations/019-notification.md)
- Роуты/вкладки: [reference/routes-by-role.md](../../reference/routes-by-role.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Вкладки — по [reference/routes-by-role.md](../../reference/routes-by-role.md), не выдуманы.
- [x] Визуальные источники — mhtml указаны (часть — только Dark/En).
- [ ] Ревью вторым человеком.
