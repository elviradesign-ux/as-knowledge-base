---
title: "Супервайзер проверяет карточку товара"
slug: supervisor-checks-product-card
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Supervisor]
roles: [Supervisor]
modules: [Product Research]
entities: [Product Card, Product, ASIN, Supplier]
workflows: [WF-002, WF-004]
related_screens: [SCR-180, SCR-181, SCR-124, SCR-320]
related_entities: [Product Card, Product, ASIN, Supplier]
related_articles: [070-researcher-creates-product-card, 013-product-card, 011-supplier]
seo_title: "Как супервайзеру проверить карточку товара — Seller Exchange"
seo_description: "Пошаговый сценарий: как супервайзер проверяет карточку товара, утверждает, отклоняет или отправляет байеру на поиск поставщика."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-002, WF-004)
  - SCREEN_CATALOG.md (SCR-180, SCR-181, SCR-124, SCR-320)
  - ENTITY_STATES.md (Статусы товара)
  - articles/foundations/013-product-card.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Продолжение
> [сценария ресёрчера](070-researcher-creates-product-card.md). Понятие карточки —
> в [Что такое карточка товара](../foundations/013-product-card.md).

# Супервайзер проверяет карточку товара

## Кратко

Сценарий описывает, как **Supervisor** проверяет карточку товара, поступившую от
ресёрчера (или клиента): утверждает, отклоняет, откладывает или отправляет байеру
на поиск поставщика. Сценарий: **WF-002** (публикация на биржу — **WF-004**).

## Кому и когда пригодится

- **Supervisor** — при поступлении карточки на проверку.

## Предварительные условия

- Роль Supervisor; есть карточки в разделе «Готовые к проверке».

## Шаги

1. Откройте **Готовые к проверке — от ресёрчера**
   ([SCR-180](../../SCREEN_CATALOG.md)) или **от клиента**
   ([SCR-181](../../SCREEN_CATALOG.md)).
2. Откройте карточку товара ([SCR-124](../../SCREEN_CATALOG.md)).
3. Проверьте данные и ASIN (ASIN-чекер — [SCR-320](../../SCREEN_CATALOG.md);
   неудачные ASIN — `FailedAsinsModal`).
4. Примите решение:
   - **утвердить** — статус `CHECKED_BY_SUPERVISOR`;
   - **отклонить** — `REJECTED_BY_SUPERVISOR_AT_FIRST_STEP`;
   - **временно отложить** — `TEMPORARILY_DALAYED`;
   - **отправить байеру на поиск поставщика** — `TO_BUYER_FOR_RESEARCH`.
5. По завершении поиска и повторной проверке — публикация на биржу
   (`COMPLETE_SUCCESS`, **WF-004**).

Коды статусов — [Entity States → Статусы товара](../../ENTITY_STATES.md).

## Результат

- Карточка получает статус проверки; при успехе — публикуется на биржу.
- При отправке байеру запускается [поиск поставщика](072-buyer-searches-supplier.md) (WF-003).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| ASIN не проходит проверку | Ошибка/недоступность ASIN | Разобрать `FailedAsinsModal`, настроить ASIN-чекер |
| Карточка вернулась | Отклонена/отложена супервайзером | Проверить статус и причину |

## Связанные материалы

- Предыдущий шаг: [Ресёрчер создаёт карточку](070-researcher-creates-product-card.md)
- Следующий шаг: [Байер ищет поставщика](072-buyer-searches-supplier.md)
- Концепт: [Карточка товара](../foundations/013-product-card.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-002/004).
- [x] Статусы дословно из ENTITY_STATES, не выдуманы.
- [ ] Ревью вторым человеком.
