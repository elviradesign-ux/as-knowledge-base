---
title: "Как пользоваться поддержкой"
slug: use-support
article_type: User Guide
section: User Guide
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
related_entities: [Support Ticket, Feedback]
related_articles: [support, 079-user-creates-support-ticket, 020-support-ticket]
seo_title: "Как пользоваться поддержкой в Seller Exchange"
seo_description: "Как пользоваться поддержкой в Seller Exchange: создать тикет, приложить файлы и отслеживать статус обращения до ответа."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - articles/screens/support.md
  - articles/workflows/079-user-creates-support-ticket.md
  - articles/foundations/020-support-ticket.md
validation_status: confirmed
---

> **User Guide (ru-источник).** Понятие — в
> [Что такое тикет поддержки](../foundations/020-support-ticket.md). Полный
> сценарий — [Пользователь создаёт тикет](../workflows/079-user-creates-support-ticket.md).

# Как пользоваться поддержкой

## Кратко

Если возник вопрос или проблема — создайте [тикет](../foundations/020-support-ticket.md)
в поддержку и отслеживайте его статус до ответа.

## Шаги

1. Откройте [Поддержку](../screens/support.md) ([SCR-015](../../SCREEN_CATALOG.md)).
2. Создайте тикет (`CreateTicketModal`); опишите проблему, приложите файлы.
3. Отправьте тикет.
4. Следите за статусом обращения (Новый → В обработке → Принято → Выполнено /
   Отклонено / Нужна информация — [Entity States](../../ENTITY_STATES.md)).

## Результат

- Тикет создан; ответ поддержки приходит как **Feedback** (Admin/Moderator).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Долго без ответа | Статус «В обработке» | Дождаться ответа (Feedback) |
| Не приложить файл | Ограничение формата/размера | Проверить допустимые форматы |

## Связанные материалы

- Экран: [Поддержка](../screens/support.md)
- Сценарий: [Пользователь создаёт тикет](../workflows/079-user-creates-support-ticket.md)

## Чеклист ревью

- [x] Шаги/статусы — из WORKFLOW_CATALOG/ENTITY_STATES.
- [x] Метаданные — front matter полон.
- [ ] Ревью вторым человеком.
