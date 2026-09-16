---
title: "Сообщения (чат)"
slug: messages
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Supervisor, Storekeeper, Freelancer, Admin]
roles: [Client, Buyer, Supervisor, Storekeeper, Freelancer, Admin]
modules: [Collaboration]
entities: [Message, User]
workflows: [WF-073]
related_screens: [SCR-014]
related_entities: [Message, User]
related_articles: [007-user]
seo_title: "Сообщения (чат): гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану внутреннего чата в Seller Exchange: переписка, создание нового чата, участники и пересылка сообщений."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-014)
  - reference/modals.md (CreateNewChatModal, ForwardMessagesModal)
  - WORKFLOW_CATALOG.md (WF-073)
  - figma-mcp/sources/mhtml/ (захват)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Внутренний чат платформы. Визуальный
> источник — mhtml.

# Сообщения (чат)

## Кратко

Экран внутреннего чата: переписка между пользователями платформы, создание чатов
и пересылка сообщений. Route: `/messages` (`MessagesView`,
[SCR-014](../../SCREEN_CATALOG.md)). Доступен всем ролям, кроме Researcher.

## Кому и когда пригодится

- **Все роли, кроме Researcher** — общение внутри платформы.

## Предварительные условия

- Доступ к разделу «Сообщения» (см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md)).

## Элементы экрана

- **Список чатов** и **область переписки**.
- Участники чата, вложения (галерея/файлы).

## Действия

Названия — из локализации (`actions_*`); модалки — из
[reference/modals.md](../../reference/modals.md):

- Написать сообщение в чат (сценарий **WF-073**).
- Создать новый чат — `CreateNewChatModal`.
- **Add a member to group chat** / *Добавить участника в групповой чат*.
- **Add a chat cover** / *Добавить обложку чата*.
- Переслать сообщения — `ForwardMessagesModal`.

## Результат

- Сообщение отправлено; при необходимости создан новый чат / добавлены участники.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [007-user](../foundations/007-user.md) Пользователь | Участники чата |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Client-Messages.*.mhtml` (light/dark, En/Uk) — экран чата.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Нет раздела «Сообщения» | Роль Researcher | Раздел недоступен Researcher |
| Не создаётся чат | Не выбран участник | Указать участника в `CreateNewChatModal` |

## Связанные материалы

- Концепт: [Что такое пользователь](../foundations/007-user.md)
- Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из локализации и [reference/modals.md](../../reference/modals.md).
- [x] Визуальный источник — mhtml (`Client-Messages`).
- [ ] Ревью вторым человеком.
