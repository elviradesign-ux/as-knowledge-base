---
title: "Админ настраивает права пользователя"
slug: admin-manages-permissions
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Admin]
roles: [Admin, Buyer]
modules: [Access Control]
entities: [Permission, Permission Preset, Sub-user, Role]
workflows: [WF-060]
related_screens: [SCR-302, SCR-M06]
related_entities: [Permission, Permission Preset, Sub-user]
related_articles: [permissions, users, 009-permission, 010-permission-preset]
seo_title: "Как админу настроить права пользователя — Seller Exchange"
seo_description: "Пошаговый сценарий: как администратор настраивает права пользователя или применяет пресет прав в Seller Exchange."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-060)
  - SCREEN_CATALOG.md (SCR-302, SCR-M06)
  - PERMISSIONS_MATRIX.md
  - articles/screens/permissions.md, users.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Понятия — в
> [Право доступа](../foundations/009-permission.md) и
> [Пресет прав](../foundations/010-permission-preset.md). UI-детали — в
> [Screen Guide «Права пользователей»](../screens/permissions.md).

# Админ настраивает права пользователя

## Кратко

Сценарий описывает, как **Admin** (или Buyer) настраивает доступы пользователю
или саб-пользователю — назначает разрешения или применяет
[пресет прав](../foundations/010-permission-preset.md). Сценарий: **WF-060**.

## Кому и когда пригодится

- **Admin / Buyer** — при выдаче или изменении доступа члену команды.

## Предварительные условия

- Роль с правом управления доступами (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).
- Есть пользователь/саб-пользователь для настройки.

## Шаги

1. Откройте [Права пользователей](../screens/permissions.md)
   ([SCR-302](../../SCREEN_CATALOG.md)) — или из
   [экрана «Пользователи»](../screens/users.md).
2. Выберите пользователя/саб-пользователя.
3. Назначьте разрешения (`PermissionsModal`, [SCR-M06](../../SCREEN_CATALOG.md)) —
   единичные (`SinglePermissionModal`) или групповые (`GroupPermissionModal`).
4. При необходимости примените/создайте **пресет прав** (**Save preset**).
5. Сохраните изменения.

## Результат

- Пользователь/саб-пользователь получает нужный доступ.
- Пресет доступен для повторного применения (согласованный доступ команды).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет доступа к настройке прав | Роль ≠ Admin/Buyer | Настройку ведёт Admin/Buyer |
| Права не применились к сабу | Не сохранён/не привязан пресет | Сохранить пресет и привязать саб-юзера |

## Связанные материалы

- Экраны: [Права пользователей](../screens/permissions.md), [Пользователи](../screens/users.md)
- Концепт: [Право доступа](../foundations/009-permission.md), [Пресет прав](../foundations/010-permission-preset.md)
- Доступ: [Permissions Matrix](../../PERMISSIONS_MATRIX.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md)/[PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Метаданные — front matter полон.
- [x] UI-детали — ссылками на Screen Guide, не дублируются.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-060).
- [ ] Ревью вторым человеком.
