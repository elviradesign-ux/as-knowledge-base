---
title: "Настроить команду"
slug: set-up-team
article_type: User Guide
section: User Guide
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Admin]
roles: [Client, Admin]
modules: [Users, Access Control]
entities: [Sub-user, User, Permission Preset]
workflows: [WF-060]
related_screens: [SCR-016, SCR-301, SCR-302]
related_entities: [Sub-user, Permission Preset]
related_articles: [054-manage-users-and-permissions, users, permissions, 010-permission-preset]
seo_title: "Как настроить команду в Seller Exchange"
seo_description: "Как настроить команду в Seller Exchange: добавить саб-пользователей и выдать им доступ через права и пресеты."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-016, SCR-301, SCR-302)
  - WORKFLOW_CATALOG.md (WF-060)
validation_status: confirmed
---

> **User Guide (ru-источник).** Быстрый старт командной работы. Подробное
> управление — в [Пользователи и права](054-manage-users-and-permissions.md).

# Настроить команду

## Кратко

Если работаете не в одиночку, добавьте членов команды как **саб-пользователей** и
выдайте им доступ через [пресет прав](../foundations/010-permission-preset.md).

## Предварительные условия

- Роль Client (или Admin); есть кого добавлять в команду.

## Шаги

1. Откройте [Пользователи](../screens/users.md)
   ([SCR-016](../../SCREEN_CATALOG.md)) → **Саб-пользователи**
   ([SCR-301](../../SCREEN_CATALOG.md)).
2. Добавьте саб-пользователя (`LinkSubUserModal`).
3. Выдайте доступ: примените/создайте пресет прав на экране
   [Права пользователей](../screens/permissions.md)
   ([SCR-302](../../SCREEN_CATALOG.md)).

## Результат

- Член команды добавлен и имеет нужный доступ.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Саб-юзер видит лишнее/недостаточно | Не настроен пресет | Настроить права ([подробно](054-manage-users-and-permissions.md)) |

## Связанные материалы

- Подробно: [Пользователи и права](054-manage-users-and-permissions.md)
- Сценарий: [Админ настраивает права](../workflows/078-admin-manages-permissions.md)

## Чеклист ревью

- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-060).
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
