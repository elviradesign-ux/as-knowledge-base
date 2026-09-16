---
title: "Настроить уведомления"
slug: configure-notifications
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Storekeeper, Freelancer, Admin]
roles: [Client, Buyer, Storekeeper, Freelancer, Admin]
modules: [Notifications]
entities: [Notification, Order, Box, Tariff]
workflows: []
related_screens: [SCR-013]
related_entities: [Notification, Order, Box, Tariff]
related_articles: [notifications, 019-notification]
seo_title: "Как работать с уведомлениями в Seller Exchange"
seo_description: "Как работать с уведомлениями в Seller Exchange: вкладки по заказам, коробкам, тарифам и заявкам и переход к связанным объектам."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/screens/notifications.md
  - articles/foundations/019-notification.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие — в
> [Что такое уведомление](../foundations/019-notification.md). UI-детали — в
> [Screen Guide «Уведомления»](../screens/notifications.md).

# Настроить уведомления

## Кратко

[Уведомления](../foundations/019-notification.md) держат вас в курсе событий по
заказам, коробкам, тарифам и заявкам. Они сгруппированы по вкладкам.

## Что можно делать

- Просматривать уведомления по темам (вкладки): по заказам, по коробкам, по
  тарифам коробок, сообщения по запросам, общие.
- Переходить из уведомления к связанному объекту
  ([заказ](../screens/orders-list.md), [коробка](../screens/warehouse-in-stock.md)).

Пошагово по экрану — [Уведомления](../screens/notifications.md)
([SCR-013](../../SCREEN_CATALOG.md)).

## Шаги

1. Откройте [Уведомления](../screens/notifications.md).
2. Выберите нужную вкладку.
3. Откройте уведомление → перейдите к объекту, требующему действия.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет нужной вкладки | Набор вкладок зависит от роли | У Client — 5 вкладок |
| Уведомление не открывает объект | Объект удалён/нет доступа | Проверить объект и права |

## Связанные материалы

- Экран: [Уведомления](../screens/notifications.md)
- Понятие: [Уведомление](../foundations/019-notification.md)

## Чеклист ревью

- [x] Вкладки — по [reference/routes-by-role.md](../../reference/routes-by-role.md).
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
