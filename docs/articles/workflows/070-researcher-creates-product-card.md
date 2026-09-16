---
title: "Ресёрчер создаёт карточку товара"
slug: researcher-creates-product-card
article_type: Workflow Guide
section: Workflows
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Researcher]
roles: [Researcher]
modules: [Product Research]
entities: [Product Card, Product, ASIN]
workflows: [WF-001, WF-002]
related_screens: [SCR-123, SCR-124]
related_entities: [Product Card, Product, ASIN, Supplier]
related_articles: [013-product-card, 001-product, 026-asin]
seo_title: "Как ресёрчеру создать карточку товара — Seller Exchange"
seo_description: "Пошаговый сценарий: как ресёрчер создаёт карточку товара в Seller Exchange и отправляет её на проверку супервайзеру."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - WORKFLOW_CATALOG.md (WF-001, WF-002)
  - SCREEN_CATALOG.md (SCR-123, SCR-124)
  - ENTITY_STATES.md (Статусы товара)
  - articles/foundations/013-product-card.md
validation_status: confirmed
---

> **Гайд по сценарию (ru-источник).** Понятие карточки — в
> [Что такое карточка товара](../foundations/013-product-card.md).

# Ресёрчер создаёт карточку товара

## Кратко

Сценарий описывает, как **Researcher** создаёт
[карточку товара](../foundations/013-product-card.md) и отправляет её на проверку
супервайзеру. Это первый шаг сквозной цепочки платформы. Сценарий: **WF-001**
(проверка супервайзером — **WF-002**).

## Кому и когда пригодится

- **Researcher** — при заведении нового товара-кандидата.

## Предварительные условия

- Роль Researcher; известен ASIN (или данные для его добавления).

## Шаги

1. Откройте раздел **Мои товары** ([SCR-123](../../SCREEN_CATALOG.md)).
2. Создайте карточку товара (**Add a product card** / *Добавить карточку товара*).
3. Заполните данные: [ASIN](../academy/026-asin.md), название, категорию, атрибуты
   ([SCR-124](../../SCREEN_CATALOG.md)).
4. Проверьте корректность идентификаторов (ASIN-чекер — на стороне супервайзера).
5. Отправьте карточку на проверку супервайзеру.

## Результат

- Карточка создана и переведена в статус ресёрча/на проверку
  (коды — [Entity States → Статусы товара](../../ENTITY_STATES.md),
  напр. `RESEARCHER_CREATED_PRODUCT`).
- Далее супервайзер проверяет карточку (**WF-002**).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не сохраняется карточка | Пустой/некорректный ASIN | Заполнить корректный ASIN |
| Не отправляется на проверку | Не заполнены обязательные данные | Дополнить данные карточки |

## Связанные материалы

- Концепт: [Карточка товара](../foundations/013-product-card.md),
  [Товар](../foundations/001-product.md), [ASIN](../academy/026-asin.md)
- Статусы: [Entity States](../../ENTITY_STATES.md)
- Следующий шаг: WF-002 (проверка супервайзером)

## Чеклист ревью

- [x] Терминология/статусы — по [GLOSSARY](../../GLOSSARY.md)/[ENTITY_STATES](../../ENTITY_STATES.md).
- [x] Метаданные — front matter полон.
- [x] Шаги — из [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-001).
- [x] Связь Research Product↔Idea не утверждается (NV, DM4).
- [ ] Ревью вторым человеком; желателен Screen Guide по карточке (SCR-124).
