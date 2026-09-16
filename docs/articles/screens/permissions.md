---
title: "Права пользователей"
slug: permissions
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Admin, Buyer]
roles: [Admin, Buyer]
modules: [Access Control]
entities: [Permission, Permission Preset, Role, Sub-user]
workflows: [WF-060]
related_screens: [SCR-302, SCR-M06]
related_entities: [Permission, Permission Preset, Role, Sub-user]
related_articles: [009-permission, 010-permission-preset, 008-role, users]
seo_title: "Права пользователей: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану прав пользователей в Seller Exchange: настройка разрешений и пресетов, единичные и групповые права, массовое редактирование."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-302, SCR-M06)
  - reference/modals.md (PermissionsModal, SinglePermissionModal, GroupPermissionModal)
  - PERMISSIONS_MATRIX.md
  - WORKFLOW_CATALOG.md (WF-060)
  - figma-mcp/sources/mhtml/ (захваты)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятия — в
> [Что такое право доступа](../foundations/009-permission.md) и
> [Пресет прав](../foundations/010-permission-preset.md). Визуальные источники — mhtml.

# Права пользователей

## Кратко

Экран настройки доступов: разрешения для пользователей и саб-пользователей,
единичные и групповые права, пресеты и массовое редактирование. Route:
`/user-permissions` (`UserPermissionsView`, [SCR-302](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Admin** и **Buyer** — управляют правами (по матрице доступа).

## Предварительные условия

- Роль с доступом к правам (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).
- Есть пользователи/саб-пользователи, которым назначаются права.

## Элементы экрана

- **Таблица прав** пользователей.
- **Пресеты** — переиспользуемые наборы прав
  (см. [Пресет прав](../foundations/010-permission-preset.md)).
- Единичные и групповые разрешения.

## Действия

Модалки — из [reference/modals.md](../../reference/modals.md):

- Назначить разрешения — `PermissionsModal` ([SCR-M06](../../SCREEN_CATALOG.md)).
- Единичное разрешение — `SinglePermissionModal`; групповое — `GroupPermissionModal`.
- **Add permission** / *Добавить разрешение*; **Save preset** / *Сохранить пресет*.
- Массовое редактирование прав (см. mhtml `MassEditUserPermissions`).
- Сценарий целиком — **WF-060** (настройка прав/пресета).

## Результат

- Пользователь/саб-пользователь получает нужный доступ.
- Пресет можно переиспользовать для согласованного доступа.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [users](users.md) Пользователи | Список пользователей и переход к правам |
| [SCR-M06](../../SCREEN_CATALOG.md) `PermissionsModal` | Назначение разрешений |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Admin.UsersPermissions.Light.Uk.mhtml` — права пользователей.
- `Admin.UsersPermissionsGroups.Light.Ru.mhtml` — групповые права.
- `Client.EditUserPermissions.En.Light.mhtml` — редактирование прав.
- `Client.MassEditUserPermissions.En.Light.mhtml` — массовое редактирование.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет доступа к экрану | Роль ≠ Admin/Buyer | Права настраивает Admin/Buyer |
| Долго назначать права по одному | Не используется пресет | Применить/создать пресет |
| Права не применились к сабу | Не сохранён/не привязан пресет | Сохранить пресет и привязать саб-юзера |

## Связанные материалы

- Концепт: [Право доступа](../foundations/009-permission.md), [Пресет прав](../foundations/010-permission-preset.md), [Роль](../foundations/008-role.md)
- Доступ: [Permissions Matrix](../../PERMISSIONS_MATRIX.md); Сценарий: WF-060

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md)/[PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из [reference/modals.md](../../reference/modals.md).
- [x] Визуальные источники — mhtml указаны.
- [ ] Ревью вторым человеком.
