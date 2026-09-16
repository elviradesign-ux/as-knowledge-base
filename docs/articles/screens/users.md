---
title: "Пользователи"
slug: users
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
roles: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
modules: [Users]
entities: [User, Sub-user, Permission Preset, Role]
workflows: [WF-060]
related_screens: [SCR-016, SCR-017, SCR-300, SCR-301]
related_entities: [User, Sub-user, Permission Preset]
related_articles: [007-user, 010-permission-preset, permissions]
seo_title: "Пользователи: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану «Пользователи» в Seller Exchange: команда пользователя, саб-пользователи, платформенные пользователи и переход к правам."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-016, SCR-017, SCR-300, SCR-301)
  - reference/modals.md (LinkSubUserModal, UserInfoEditModal)
  - PERMISSIONS_MATRIX.md
  - figma-mcp/sources/mhtml/ (захваты)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятия — в
> [Что такое пользователь](../foundations/007-user.md). Визуальные источники — mhtml.

# Пользователи

## Кратко

Экран «Пользователи» — управление командой: список пользователей и
саб-пользователей, их данные и переход к правам. Route: `/users`
(`SubUsersView` / `CategoryRootView`, [SCR-016](../../SCREEN_CATALOG.md)). Admin
дополнительно ведёт **пользователей платформы** и **саб-пользователей**.

## Кому и когда пригодится

- **Все роли** — видят раздел «Пользователи».
- **Admin** — управляет пользователями платформы и правами.

## Предварительные условия

- Доступ к разделу (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).

## Элементы экрана

- **Список пользователей / саб-пользователей** (таблица).
- **Детали пользователя** — [SCR-017](../../SCREEN_CATALOG.md) (`AnotherUserView`).
- Для Admin: **Пользователи платформы** ([SCR-300](../../SCREEN_CATALOG.md)),
  **Саб-пользователи** ([SCR-301](../../SCREEN_CATALOG.md)).

## Действия

Названия — из локализации (`actions_*`); модалки — из
[reference/modals.md](../../reference/modals.md):

- **Add a user** / *Добавить пользователя*, **Add a sub-user** / *Добавить саб-юзера*
  (привязка — `LinkSubUserModal`).
- Редактировать данные пользователя — `UserInfoEditModal`.
- Открыть профиль другого пользователя — `AnotherUserView`.
- **Add a preset** / *Добавить пресет* — типовой набор прав
  (см. [Пресет прав](../foundations/010-permission-preset.md)).
- Перейти к правам — экран [Права пользователей](permissions.md).

## Результат

- Пользователь/саб-пользователь добавлен в команду.
- Доступ уточняется ролью и пресетом (см. [Пользователь](../foundations/007-user.md)).

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-017](../../SCREEN_CATALOG.md) Детали пользователя | Данные конкретного пользователя |
| [permissions](permissions.md) Права пользователей | Настройка доступов |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Client-Users.Dark.En.mhtml`, `Client.Users.En.Light.mhtml` — список пользователей.
- `Client.Users.NewPreset.Light.En.mhtml` — создание пресета.
- `Client-AnotherUserProfile.*.mhtml` (light/dark, En/Uk) — профиль пользователя.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не могу добавить пользователя | Нет прав | Проверить роль (управление — у Admin) |
| Саб-юзер не видит нужное | Ограничены права/продукты/магазины | Настроить права (`permissions`) |
| Нет раздела «Пользователи платформы» | Роль ≠ Admin | Раздел доступен Admin |

## Связанные материалы

- Концепт: [Что такое пользователь](../foundations/007-user.md), [Пресет прав](../foundations/010-permission-preset.md)
- Доступ: [Permissions Matrix](../../PERMISSIONS_MATRIX.md); Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md); роли — [PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из локализации и [reference/modals.md](../../reference/modals.md).
- [x] Визуальные источники — mhtml указаны.
- [ ] Ревью вторым человеком.
