---
title: "Что такое заявка на услугу"
slug: service-request
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Freelancer]
modules: [Freelance]
entities: [Service Request, Proposal, Service, Milestone]
workflows: [WF-033, WF-050]
related_screens: [SCR-260, SCR-261, SCR-262]
related_entities: [Proposal, Service, Milestone]
related_articles: [016-proposal, 007-user]
seo_title: "Заявка на услугу в Seller Exchange — запрос на бирже услуг"
seo_description: "Что такое заявка на услугу в Seller Exchange: запрос клиента на бирже услуг, на который откликаются фрилансеры своими предложениями."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Service Request, Proposal, Service)
  - ENTITY_RELATIONSHIPS.md (#54, #55, #56, #57, #99)
  - SCREEN_CATALOG.md (SCR-260, SCR-261, SCR-262)
  - WORKFLOW_CATALOG.md (WF-033, WF-050)
validation_status: confirmed
---

> **Канонический источник (ru).** Переводы создаются из этого файла после
> отдельного решения. При правках сначала меняем источник.

# Что такое заявка на услугу

**Заявка на услугу** (Service Request) — запрос клиента на бирже услуг. На заявку
откликаются фрилансеры (Service Provider) своими предложениями.

## Кратко

Заявка описывает, какая услуга нужна клиенту для запуска на Amazon. Фрилансеры
видят заявку и отправляют по ней предложения; клиент выбирает подходящее.

## Что это такое

Заявка — единица спроса на бирже услуг. Она относится к услуге, получает
предложения (Proposal) и может иметь вехи (Milestone) для контроля прогресса.

## Зачем это нужно

- Клиент формулирует потребность в услуге в одном месте.
- Фрилансеры откликаются предложениями — есть из чего выбрать.
- Вехи помогают отслеживать выполнение.

## Основные атрибуты

- **Услуга** — к какой услуге относится заявка.
- **Предложения** — отклики фрилансеров.
- **Вехи (Milestone)** — контрольные точки прогресса.

## Жизненный цикл и статусы

Отдельного набора числовых статус-кодов у заявки в базе знаний нет. Заявки
разделяются по виду (`kind`): «мои» (MY) и «вакантные» (VACANT).

## Связи с другими сущностями

- Заявка **создаётся** клиентом.
- Заявка **получает** предложения (Proposal).
- Заявка **ссылается** на услугу и **имеет** вехи (Milestone).

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

- **Client** — создаёт заявки и выбирает предложения.
- **Freelancer** — видит вакантные заявки и откликается.

Доступ — см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-260](../../SCREEN_CATALOG.md) Биржа услуг (Client) | Создание/просмотр заявок |
| [SCR-261](../../SCREEN_CATALOG.md) Мои запросы (Client) | Свои заявки |
| [SCR-262](../../SCREEN_CATALOG.md) Вакантные запросы (Freelancer) | Заявки для откликов |

Заявка открывается в модалках `RequestModal`, `CreateRequestModal`.

## Связанные сценарии

- **WF-033** — запрос на бирже услуг фрилансерам (Client).
- **WF-050** — отклик на вакантный запрос предложением (Freelancer).

## Термины и справочники

- Связи: [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).
- Вехи: [Entity States / DOMAIN_MODEL](../../DOMAIN_MODEL.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Чем заявка отличается от предложения? | Заявка — спрос клиента; предложение (Proposal) — отклик фрилансера на заявку. |
| Что такое вакантные заявки? | Заявки, доступные фрилансерам для отклика (`kind=VACANT`). |
| Кто создаёт заявку? | Client. |

## Связанные статьи

- [016 — Предложение](016-proposal.md)
- [007 — Пользователь](007-user.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Не выдуманы статусы заявки (числовых кодов в КБ нет) — описан `kind`.
- [x] Экраны/сценарии подтверждены (SCR-260…262, WF-033/050).
- [x] Внутренние ссылки корректны.
