---
title: "Пользователи и права"
slug: manage-users-and-permissions
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Admin, Client]
roles: [Admin, Client, Buyer]
modules: [Users, Access Control]
entities: [User, Sub-user, Permission, Permission Preset, Role]
workflows: [WF-060]
related_screens: [SCR-016, SCR-017, SCR-300, SCR-301, SCR-302]
related_entities: [User, Permission Preset, Role]
related_articles: [048-set-up-team, users, permissions, 078-admin-manages-permissions, 009-permission, 010-permission-preset]
seo_title: "Управление пользователями и правами в Seller Exchange"
seo_description: "Как управлять пользователями и правами в Seller Exchange: роли, саб-пользователи, разрешения и пресеты прав."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/screens/users.md, permissions.md
  - articles/workflows/078-admin-manages-permissions.md
  - PERMISSIONS_MATRIX.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятия — в
> [Роль](../foundations/008-role.md), [Право](../foundations/009-permission.md),
> [Пресет прав](../foundations/010-permission-preset.md).

# Пользователи и права

## Кратко

Управляйте командой: добавляйте пользователей и саб-пользователей, назначайте
[роли](../foundations/008-role.md) и настраивайте
[права](../foundations/009-permission.md) через
[пресеты](../foundations/010-permission-preset.md).

## Что можно делать

- **Пользователи** — [экран «Пользователи»](../screens/users.md)
  ([SCR-016](../../SCREEN_CATALOG.md)): список, детали, саб-пользователи; Admin —
  пользователи платформы ([SCR-300](../../SCREEN_CATALOG.md)).
- **Права** — [экран «Права пользователей»](../screens/permissions.md)
  ([SCR-302](../../SCREEN_CATALOG.md)): единичные и групповые разрешения, пресеты,
  массовое редактирование.

## Шаги (типовой сценарий)

1. Добавьте пользователя/саб-пользователя ([Пользователи](../screens/users.md)).
2. Назначьте права или примените пресет ([Права](../screens/permissions.md)).
3. Сохраните — доступ применяется.

Полный сценарий — [Админ настраивает права](../workflows/078-admin-manages-permissions.md).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет доступа к настройке прав | Роль ≠ Admin/Buyer | Настройку ведёт Admin/Buyer |
| Права не применились | Не сохранён/не привязан пресет | Сохранить пресет и привязать |

## Связанные материалы

- Быстрый старт: [Настроить команду](048-set-up-team.md)
- Матрица доступа: [Permissions Matrix](../../PERMISSIONS_MATRIX.md)

## Чеклист ревью

- [x] UI/действия — ссылками на Screen/Workflow Guides.
- [x] Роли/доступ — по [PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
