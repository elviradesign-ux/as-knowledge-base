---
title: "Что такое партия"
slug: batch
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: draft
difficulty: beginner
locale: ru
audience: [Новые продавцы, Команда платформы]
roles: [Client, Storekeeper, Admin]
modules: [Batches, Warehouse]
entities: [Batch, Box, Shipment, Product, Order]
workflows: [WF-035, WF-041]
related_screens: [SCR-240, SCR-241, SCR-242]
related_entities: [Box, Shipment]
related_articles: [004-box, 003-order]
seo_title: "Партия в Seller Exchange — группировка коробок для отправки"
seo_description: "Что такое партия в Seller Exchange: группа коробок, отправляемых вместе на Amazon, её статусы (ожидающие, отправленные, архив) и Prep ID."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [ru, en, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Batch, §8 lifecycle)
  - ENTITY_RELATIONSHIPS.md (#46, #47)
  - ENTITY_STATES.md (Статусы товара на складе/отгрузки — контекст)
  - GLOSSARY.md (Партия)
  - SCREEN_CATALOG.md (SCR-240, SCR-241, SCR-242)
  - WORKFLOW_CATALOG.md (WF-035, WF-041)
validation_status: "partial — жизненный цикл партии нужно уточнить (DM8)"
---

> **Черновик (draft), язык-источник ru.** Не финализировать до закрытия **DM8**
> (жизненный цикл партии) и вопроса о сущности **Shipment**. Плейсхолдеры и
> source notes — для автора; финальную прозу пишем после валидации.

# Что такое партия

## Кратко
_TODO (1–2 предложения): партия — это группа коробок, отправляемых вместе на
Amazon; несёт Prep ID._
> Источник: DOMAIN_MODEL §4 «Batch»; GLOSSARY «Партия».

## Описание
_TODO: партия группирует коробки для одной отправки._
> Источник: DOMAIN_MODEL §4 «Batch».

## Зачем это нужно
_TODO: партия — единица отправки, консолидирующая коробки в inbound на Amazon._

## Жизненный цикл и статусы
_TODO: описать статусные вкладки (ожидающие отправки → отправленные → архив)._
> ⚠️ **Needs validation (DM8):** точные числовые коды статусов и переходы для
> партии пока не задокументированы — запросить у техлида перед финализацией.
> Источник: DOMAIN_MODEL §8; SCREEN_CATALOG (SCR-240…242).

## Как связано с другими понятиями
- Партия **группирует** коробки.
- Партия **отправляется как** Shipment _(Shipment как сущность — Needs validation)_.
> Источник: ENTITY_RELATIONSHIPS #46, #47.

## Кто с ним работает
_TODO: Client, Storekeeper, Admin._
> Источник: PERMISSIONS_MATRIX.

## Где вы это видите
- [SCR-240](../../SCREEN_CATALOG.md) Партии — ожидающие отправки
- [SCR-241](../../SCREEN_CATALOG.md) Партии — отправленные
- [SCR-242](../../SCREEN_CATALOG.md) Партии — архив
> Источник: SCREEN_CATALOG.

## Связанные сценарии
- **WF-035** — отправка коробок в партию (Client).
- **WF-041** — формирование и отправка партии (Storekeeper).
> Источник: WORKFLOW_CATALOG.

## Термины глоссария
_TODO:_ [Партия](../../GLOSSARY.md), [Коробка](../../GLOSSARY.md).

## Частые вопросы
| Вопрос | Ответ |
|---|---|
| Что такое Prep ID? | _TODO._ |
| _TODO_ | _TODO_ |

## Связанные статьи
- [004 — Коробка](004-box.md)
- [003 — Заказ](003-order.md)

## Чеклист автора (перед ревью)
- [ ] `validation_status` = partial до ответа по DM8.
- [ ] НЕ выдумывать коды статусов партии — ждать DM8.
- [ ] Связи проставлены ссылками, не дублируются.
- [ ] Скриншоты без реальных ПДн.
- [ ] EN-перевод создаём только после финализации RU-источника.
