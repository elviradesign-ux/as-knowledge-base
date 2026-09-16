---
title: "Поддержка"
slug: support
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
roles: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
modules: [Support]
entities: [Support Ticket, Feedback]
workflows: [WF-072]
related_screens: [SCR-015]
related_entities: [Support Ticket, Feedback, User]
related_articles: [020-support-ticket]
seo_title: "Поддержка: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану поддержки в Seller Exchange: создание тикета, просмотр обращений и их статусов, ответ поддержки."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-015)
  - reference/modals.md (CreateTicketModal, TicketModal)
  - ENTITY_STATES.md (Статус обращения)
  - WORKFLOW_CATALOG.md (WF-072)
  - figma-mcp/sources/mhtml/ (захват)
validation_status: confirmed
---

> **Гайд по экрану (ru-источник).** Понятие тикета — в
> [Что такое тикет поддержки](../foundations/020-support-ticket.md). Визуальный
> источник — mhtml.

# Поддержка

## Кратко

Экран поддержки: создание обращений (тикетов) и отслеживание их статусов. Route:
`/support` (`SupportView`, [SCR-015](../../SCREEN_CATALOG.md)). Доступен всем ролям.

## Кому и когда пригодится

- **Все роли** — создают тикеты в поддержку.
- **Admin / Moderator** — обрабатывают тикеты (ответ = Feedback).

## Предварительные условия

- Доступ к разделу «Поддержка» (доступен всем).

## Элементы экрана

- **Список тикетов** с их статусами.
- Статусы обращения — по [Entity States](../../ENTITY_STATES.md)
  (Новый → В обработке → Принято → Выполнено / Отклонено / Нужна информация).

## Действия

Модалки — из [reference/modals.md](../../reference/modals.md):

- Создать тикет — `CreateTicketModal` (сценарий **WF-072**); можно приложить файлы.
- Открыть тикет — `TicketModal`.
- Ответ поддержки фиксируется как **Feedback** (Admin/Moderator, DM9).

## Результат

- Тикет создан и виден в списке; проходит статусы обработки до «Выполнено» или
  «Отклонено».

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [020-support-ticket](../foundations/020-support-ticket.md) Тикет поддержки | Понятие тикета и статусы |

## Визуальные источники (mhtml)

- `Client-Support.Dark.En.mhtml` — экран поддержки _(только Dark/En)_.

> Желательны захваты в Light-теме и других языках.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Тикет долго без ответа | Ждёт обработки поддержкой | Статус «В обработке»; дождаться ответа (Feedback) |
| Не приложить файл | Ограничение формата/размера | Проверить допустимые форматы вложений |

## Связанные материалы

- Концепт: [Что такое тикет поддержки](../foundations/020-support-ticket.md)
- Статусы: [Entity States](../../ENTITY_STATES.md); Сценарий: WF-072

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из [reference/modals.md](../../reference/modals.md).
- [x] Визуальный источник — mhtml (только Dark/En).
- [ ] Ревью вторым человеком; желательны Light/иные языки.
