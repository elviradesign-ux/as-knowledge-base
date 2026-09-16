---
title: "Что такое Seller Exchange"
slug: what-is-seller-exchange
article_type: SEO / Pillar
section: Pillar
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Внешняя аудитория, Команда платформы]
roles: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
modules: [Inventory, Orders, Warehouse, Suppliers, Freelance, Analytics, Users, Integrations]
entities: [Product, Order, Box, Batch, Supplier, User]
workflows: []
related_screens: []
related_entities: [Product, Inventory, Order, Box, Supplier, User, Role]
related_articles: [001-product, 002-inventory, 003-order, 004-box, 007-user, 008-role, 025-marketplace-terms]
seo_title: "Что такое Seller Exchange — платформа для продавцов Amazon"
seo_description: "Что такое Seller Exchange: мульти-ролевая платформа для продавцов Amazon — товары, заказы, инвентарь, склады, поставщики и аналитика в одном месте."
owner: TBD
last_updated: 2026-07-08
review_by: 2026-10-08
locales: [en, ru, zh, ua]
source_documents:
  - MANIFESTO.md
  - DOMAIN_MODEL.md
  - INFORMATION_ARCHITECTURE.md
validation_status: confirmed
---

> **Pillar-статья (ru-источник).** Обзорная страница, связывающая ключевые
> разделы базы знаний. Факты — из [MANIFESTO](../../MANIFESTO.md) и
> [DOMAIN_MODEL](../../DOMAIN_MODEL.md); детали — в связанных статьях.

# Что такое Seller Exchange

**Seller Exchange** (внутр. кодовое имя — AmazonService / AS) — мульти-ролевая
SaaS-платформа для продавцов Amazon. Её задача — объединить в одном рабочем
пространстве то, для чего обычно нужны 5–10 отдельных инструментов: товары,
заказы, инвентарь, склады, поставщиков, аналитику и командную работу.

## Из чего состоит платформа

### Ключевые сущности
- [Товар](../foundations/001-product.md) — центральная сущность каталога.
- [Инвентарь](../foundations/002-inventory.md) — каталог товаров с аналитикой.
- [Заказ](../foundations/003-order.md) — запрос на закупку.
- [Коробка](../foundations/004-box.md) — единица склада и отправки.

Полный словарь — [Термины маркетплейса](../academy/025-marketplace-terms.md).

### Роли и доступ
Платформа использует ролевую модель (RBAC): [пользователь](../foundations/007-user.md)
имеет [роль](../foundations/008-role.md), которая определяет доступ. Восемь
продуктовых ролей — от Client до Admin (см.
[Permissions Matrix](../../PERMISSIONS_MATRIX.md)).

### Модули
Инвентарь и товары, заказы, склад и партии, поставщики и биржи, запуск товаров,
финансы, уведомления, поддержка, аналитика и реклама, интеграции. Карта модулей —
[INFORMATION_ARCHITECTURE](../../INFORMATION_ARCHITECTURE.md).

## Как это работает (в двух словах)

Товар проходит цепочку по ролям: ресёрчер создаёт карточку → супервайзер
проверяет → байер находит поставщика → клиент создаёт заказ → байер обрабатывает
→ сторкипер принимает коробки. Подробно — в
[Полном гайде по построению Amazon-бизнеса](081-complete-guide-amazon-business.md).

## Что почитать дальше

- [Полный гайд по построению Amazon-бизнеса](081-complete-guide-amazon-business.md)
- [Единое рабочее пространство для операций](086-one-workspace.md)
- [Как управлять запасами Amazon](083-how-to-manage-inventory.md)
- [Как организовать команду продавца](085-organize-seller-team.md)

## Связанные материалы

- Термины: [Термины маркетплейса](../academy/025-marketplace-terms.md)
- Модель: [DOMAIN_MODEL](../../DOMAIN_MODEL.md); Доступ: [Permissions Matrix](../../PERMISSIONS_MATRIX.md)

## Чеклист ревью

- [x] Факты — из [MANIFESTO](../../MANIFESTO.md)/[DOMAIN_MODEL](../../DOMAIN_MODEL.md), без выдумок.
- [x] Тон educational, без маркетинговых преувеличений.
- [x] Метаданные — front matter полон.
- [x] Ссылки на существующие статьи.
- [ ] SEO/маркетинг-ревью перед публикацией.
