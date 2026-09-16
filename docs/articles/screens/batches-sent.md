---
title: "Партии — отправленные"
slug: batches-sent
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Storekeeper, Admin]
roles: [Client, Storekeeper, Admin]
modules: [Batches]
entities: [Batch, Box, Shipment]
workflows: [WF-041]
related_screens: [SCR-241, SCR-242]
related_entities: [Batch, Box, Shipment]
related_articles: [005-batch, 004-box]
seo_title: "Партии — отправленные: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану отправленных партий в Seller Exchange: список отправленных партий, детали партии и архив."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-241, SCR-242)
  - reference/modals.md (BatchInfoModal, BatchMoreInfoModal, EditBatchModal)
  - figma-mcp/sources/mhtml/ (захваты)
validation_status: "confirmed (жизненный цикл партии — Needs validation, DM8)"
---

> **Гайд по экрану (ru-источник).** Понятие партии — в
> [Что такое партия](../foundations/005-batch.md) _(draft/blocked DM8)_.
> Визуальные источники — mhtml.

# Партии — отправленные

## Кратко

Экран показывает **отправленные партии** — группы коробок, уже ушедшие на Amazon,
с возможностью открыть детали партии и архив. Route: `/batches/sent-batches`
(`SentBatchesView`, [SCR-241](../../SCREEN_CATALOG.md)); архив —
`/batches/sent-batches/archive` ([SCR-242](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Client** — отслеживать свои отправленные партии.
- **Storekeeper / Admin** — в рамках складских операций и надзора.

## Предварительные условия

- Есть отправленные партии (иначе список пуст).

## Элементы экрана

- **Таблица отправленных партий** (CustomDataGrid).
- **Детали партии** — состав коробок, Prep ID
  (см. mhtml `...-BatchDetail`).
- **Архив** отправленных партий ([SCR-242](../../SCREEN_CATALOG.md)).

> ⚠️ Числовые статусы/переходы партии в базе знаний не зафиксированы —
> **Needs validation (DM8)**; здесь описан экран, не жизненный цикл.

## Действия

Модалки — из [reference/modals.md](../../reference/modals.md):

- Открыть информацию о партии — `BatchInfoModal`, `BatchMoreInfoModal`.
- Редактировать партию — `EditBatchModal` (в применимых случаях).
- Перейти к архиву отправленных партий.

## Результат

- Видно, какие партии отправлены и что в них входит.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [005-batch](../foundations/005-batch.md) Партия | Понятие партии (blocked DM8) |
| [004-box](../foundations/004-box.md) Коробка | Что входит в партию |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/`:

- `Client-BatchesSent.*.mhtml` (light/dark, En/Uk) — список отправленных.
- `Client-SentBatches.*.mhtml` — отправленные партии.
- `Client-BatchesSent-BatchDetail.*.mhtml` — детали партии.

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Пустой список | Нет отправленных партий | Сформировать и отправить партию (по DM8) |
| Не открывается деталь | Нет доступа/партия в архиве | Проверить права и раздел «Архив» |

## Связанные материалы

- Концепт: [Что такое партия](../foundations/005-batch.md), [Коробка](../foundations/004-box.md)
- Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Действия/модалки — из [reference/modals.md](../../reference/modals.md).
- [x] Визуальные источники — mhtml указаны.
- [x] Жизненный цикл партии помечен *Needs validation* (DM8), не выдуман.
- [ ] Ревью вторым человеком.
