---
title: "Пользователь создаёт тикет в поддержку"
slug: user-creates-support-ticket
article_type: Workflow Guide
section: Workflows
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
related_articles: [support, 020-support-ticket]
seo_title: "Как создать тикет в поддержку — Seller Exchange"
seo_description: "Пошаговый сценарий: как пользователь создаёт тикет в поддержку в Seller Exchange и отслеживает его статус до ответа."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-072)
  - SCREEN_CATALOG.md (SCR-015)
  - ENTITY_STATES.md (Статус обращения)
  - articles/screens/support.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Понятие тикета — в
> [Что такое тикет поддержки](../foundations/020-support-ticket.md). UI-детали —
> в [Screen Guide «Поддержка»](../screens/support.md).

# Пользователь создаёт тикет в поддержку

## Кратко

Сценарий описывает, как пользователь любой роли создаёт обращение (тикет) в
поддержку и отслеживает его статус до ответа. Сценарий: **WF-072**.

## Кому и когда пригодится

- **Любая роль** — при вопросе или проблеме, требующей поддержки.

## Предварительные условия

- Доступ к разделу «Поддержка» (доступен всем).

## Шаги

1. Откройте [Поддержку](../screens/support.md) ([SCR-015](../../SCREEN_CATALOG.md)).
2. Создайте тикет (`CreateTicketModal`).
3. Опишите проблему; при необходимости приложите файлы.
4. Отправьте тикет.
5. Отслеживайте статус обращения в списке тикетов.

## Результат

- Тикет создан со статусом «Новый» и проходит обработку
  (Новый → В обработке → Принято → Выполнено / Отклонено / Нужна информация —
  [Entity States](../../ENTITY_STATES.md)).
- Ответ поддержки приходит как **Feedback** (Admin/Moderator, DM9).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Тикет долго без ответа | Статус «В обработке» | Дождаться ответа (Feedback) |
| Не приложить файл | Ограничение формата/размера | Проверить допустимые форматы вложений |

## Связанные материалы

- Экран: [Поддержка](../screens/support.md)
- Концепт: [Тикет поддержки](../foundations/020-support-ticket.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] UI-детали — ссылкой на Screen Guide, не дублируются.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-072).
- [ ] Ревью вторым человеком.
