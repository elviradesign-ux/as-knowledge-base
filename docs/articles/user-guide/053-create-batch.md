---
title: "Создать партию"
slug: create-batch
article_type: User Guide
section: User Guide
status: blocked
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Storekeeper]
roles: [Client, Storekeeper]
modules: [Batches, Warehouse]
entities: [Batch, Box, Shipment]
workflows: [WF-035, WF-041]
related_screens: [SCR-240, SCR-241]
related_entities: [Batch, Box, Shipment]
related_articles: [052-manage-boxes, 005-batch, 076-client-sends-boxes-into-batch, 077-storekeeper-forms-batch]
seo_title: "Как создать партию в Seller Exchange (в подготовке)"
seo_description: "Инструкция по созданию партии в Seller Exchange. Заблокирована до уточнения жизненного цикла партии (DM8)."
owner: TBD
last_updated: 2026-07-09
review_by: 2026-10-09
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-035, WF-041)
  - DOMAIN_MODEL.md (§8 Batch; §11)
  - DOMAIN_MODEL_OPEN_QUESTIONS.md (DM8)
validation_status: "blocked (DM8)"
---

> ⚠️ **BLOCKED.** Инструкция не пишется до уточнения жизненного цикла **партии** и
> сущности **Shipment**. Ниже — причина и что нужно закрыть.

# Создать партию — BLOCKED

## Статус: BLOCKED (DM8)

Инструкция описывает, как пользователь формирует и отправляет
[партию](../foundations/005-batch.md) из коробок. Она опирается на статусы партии,
которые **пока не подтверждены**.

## Причина блокировки

- **Жизненный цикл партии не задокументирован** — нет числовых статусов и
  переходов (только вкладки ожидающие/отправленные/архив). См.
  [ENTITY_STATES](../../ENTITY_STATES.md), [DOMAIN_MODEL §8](../../DOMAIN_MODEL.md).
- **Shipment не подтверждён** как сущность или жизненный цикл коробки
  ([DOMAIN_MODEL §11](../../DOMAIN_MODEL.md)).

## Какие вопросы нужно закрыть

1. **DM8 — Batch lifecycle:** статусы партии и переходы; генерация Prep ID.
2. **Shipment:** сущность или жизненный цикл коробки.
3. **Границы ролей** (клиент vs сторкипер) — WF-035 vs WF-041.

Трекер — [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md).

## Черновой каркас (заполнить после DM8)

- **Кратко:** _TODO._
- **Предварительные условия:** [коробки готовы](052-manage-boxes.md).
- **Шаги:** _TODO_ (собрать коробки в партию → Prep ID → отправить).
- **Результат:** _TODO_ (партия отправлена; см.
  [Отправленные партии](../screens/batches-sent.md)).

## Связанные материалы

- Сценарии (blocked): [Клиент отправляет коробки в партию](../workflows/076-client-sends-boxes-into-batch.md),
  [Сторкипер формирует партию](../workflows/077-storekeeper-forms-batch.md)
- Открытые вопросы: [DOMAIN_MODEL_OPEN_QUESTIONS](../../DOMAIN_MODEL_OPEN_QUESTIONS.md) (DM8)

## Чеклист (разблокировка)

- [ ] DM8 — Batch lifecycle подтверждён.
- [ ] Shipment — решено (сущность/lifecycle).
- [ ] Написать шаги и перевести в `review`/`approved`.
