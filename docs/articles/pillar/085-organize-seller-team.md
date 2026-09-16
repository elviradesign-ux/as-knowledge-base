---
title: "Как организовать команду Amazon-продавца"
slug: organize-seller-team
article_type: SEO / Pillar
section: Pillar
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Продавцы, Внешняя аудитория, Команда платформы]
roles: [Admin, Client]
modules: [Users, Access Control]
entities: [User, Sub-user, Role, Permission, Permission Preset]
workflows: [WF-060]
related_screens: [SCR-302]
related_entities: [User, Role, Permission Preset]
related_articles: [007-user, 008-role, 009-permission, 010-permission-preset, users, permissions, 078-admin-manages-permissions]
seo_title: "Как организовать команду Amazon-продавца — Seller Exchange"
seo_description: "Как организовать команду продавца Amazon в Seller Exchange: роли, саб-пользователи, права доступа и переиспользуемые пресеты прав."
owner: TBD
last_updated: 2026-07-08
review_by: 2026-10-08
locales: [en, ru, zh, ua]
source_documents:
  - PERMISSIONS_MATRIX.md
  - articles/foundations/007-user.md, 008-role.md, 009-permission.md, 010-permission-preset.md
validation_status: confirmed
---

> **Pillar-статья (ru-источник).** Обзор командной работы и доступов. Детали — в
> связанных статьях.

# Как организовать команду Amazon-продавца

Seller Exchange рассчитан на командную работу: одни данные показываются разным
ролям по-разному, а доступ настраивается гибко.

## Из чего складывается команда

### Пользователи и саб-пользователи
[Пользователь](../foundations/007-user.md) — участник платформы; членов команды
добавляют как **саб-пользователей** (возможны у роли любого типа).

### Роли
[Роль](../foundations/008-role.md) задаёт базовый доступ (RBAC). Восемь
продуктовых ролей — от Client до Admin (см.
[Permissions Matrix](../../PERMISSIONS_MATRIX.md)).

### Права и пресеты
[Права доступа](../foundations/009-permission.md) уточняют, что можно делать;
[пресет прав](../foundations/010-permission-preset.md) — переиспользуемый набор
для быстрого и согласованного доступа.

## Как настроить доступ

1. Добавьте пользователей/саб-пользователей — экран
   [Пользователи](../screens/users.md).
2. Настройте права или примените пресет — экран
   [Права пользователей](../screens/permissions.md). →
   [Админ настраивает права (WF-060)](../workflows/078-admin-manages-permissions.md).

## Что почитать дальше

- [Что такое Seller Exchange](080-what-is-seller-exchange.md)
- [Единое рабочее пространство для операций](086-one-workspace.md)

## Чеклист ревью

- [x] Роли/доступ — по [PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Тон educational, без маркетинга.
- [x] Ссылки на существующие статьи.
- [ ] SEO/маркетинг-ревью перед публикацией.
