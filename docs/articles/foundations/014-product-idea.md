---
title: "Что такое идея"
slug: product-idea
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer]
modules: [Product Launch]
entities: [Product Idea, Product, Supplier Search Request, Milestone]
workflows: [WF-032]
related_screens: [SCR-140, SCR-141, SCR-142, SCR-146, SCR-M07]
related_entities: [Product, Product Card, Supplier Search Request, Milestone]
related_articles: [013-product-card, 001-product, 011-supplier]
seo_title: "Идея в Seller Exchange — кандидат на запуск товара"
seo_description: "Что такое идея в Seller Exchange: кандидат на запуск товара в модуле Product Launch, её пайплайн статусов от новой идеи до реализованной или отклонённой."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Product Idea)
  - ENTITY_RELATIONSHIPS.md (#21, #22, #23, #100)
  - ENTITY_STATES.md (Статусы идеи)
  - SCREEN_CATALOG.md (SCR-140…146, SCR-M07)
  - WORKFLOW_CATALOG.md (WF-032)
validation_status: confirmed
---

> **Канонический источник (ru).** Переводы создаются из этого файла после
> отдельного решения. При правках сначала меняем источник.

# Что такое идея

**Идея** (Product Idea) — кандидат на запуск товара. В модуле «Запуск товаров»
(Product Launch) идея проходит воронку от первичной задумки до реализованного
товара или отклонения.

## Кратко

Идея — это способ провести потенциальный товар через этапы проверки и подготовки:
от новой идеи, через проверку и поиск поставщика, до создания карточки и запуска.
Идеи собраны в отдельном разделе и управляются модалкой идеи.

## Что это такое

Идея — рабочая единица запуска товара. Она связана с товаром, порождает запрос на
поиск поставщика и продвигается по вкладкам пайплайна.

## Зачем это нужно

- Даёт воронку отбора товаров к запуску.
- Связывает воедино проверку, поиск поставщика и создание карточки.
- Помогает не терять кандидатов: у каждой идеи есть статус и место в пайплайне.

## Основные атрибуты

- **Товар** — с каким товаром связана идея.
- **Статус** — этап пайплайна (см. ниже).
- **Вехи (Milestone)** — контрольные точки прогресса идеи.

## Жизненный цикл и статусы

Идея проходит пайплайн запуска, примерно:

> New → On checking → Supplier search → Supplier found / not found →
> Card creating → Adding ASIN → Realized / Rejected / Closed

Полные значения — в [Entity States → Статусы идеи](../../ENTITY_STATES.md); здесь
не дублируются.

## Связи с другими сущностями

- Идея **ссылается** на товар.
- Идея **порождает** запрос на поиск поставщика.
- К идее **крепятся** вехи (Milestone).

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

- **Client** — заводит идеи и ведёт их по пайплайну.
- **Buyer** — участвует на этапе поиска поставщика.

Доступ — см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-140](../../SCREEN_CATALOG.md) Запуск товаров — все | Все идеи |
| [SCR-141](../../SCREEN_CATALOG.md) Новые идеи | Новые кандидаты |
| [SCR-142](../../SCREEN_CATALOG.md) На проверке | Идеи на проверке |
| [SCR-146](../../SCREEN_CATALOG.md) Запуск товаров (Buyer) | Идеи со стороны байера |
| [SCR-M07](../../SCREEN_CATALOG.md) Модалка идеи (`IdeaModal`) | Работа с идеей |

## Связанные сценарии

- **WF-032** — создание идеи и прохождение пайплайна запуска (Client).

## Термины и справочники

- Термины: [Идея / Запуск товара](../../GLOSSARY.md).
- Статусы: [Entity States](../../ENTITY_STATES.md).
- Связи: [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Идея и карточка товара — одно и то же? | Нет. Идея — кандидат на запуск; на этапе «Card creating» под неё создаётся карточка товара. |
| Что происходит с отклонённой идеей? | Она переходит в статус Rejected/Closed (см. Entity States). |
| Кто ведёт идею? | Client; на этапе поиска поставщика подключается Buyer. |

## Связанные статьи

- [013 — Карточка товара](013-product-card.md)
- [001 — Товар](001-product.md)
- [011 — Поставщик](011-supplier.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования справочников — статусы даны ссылкой.
- [x] Экраны/сценарии подтверждены (SCR-140…146, SCR-M07, WF-032).
- [x] Внутренние ссылки корректны.
