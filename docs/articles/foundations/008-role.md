---
title: "Что такое роль"
slug: role
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Buyer, Supervisor, Researcher, Storekeeper, Freelancer, Admin]
modules: [Access Control, Users]
entities: [Role, Permission, Permission Preset, User]
workflows: [WF-060]
related_screens: [SCR-302]
related_entities: [User, Permission, Permission Preset]
related_articles: [007-user, 009-permission, 010-permission-preset]
seo_title: "Роль в Seller Exchange — модель доступа (RBAC)"
seo_description: "Что такое роль в Seller Exchange: предопределённая модель доступа (RBAC), список ролей платформы и их коды, а также расхождения терминологии между дизайном и бэкендом."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 Role)
  - ENTITY_STATES.md (Коды ролей)
  - PERMISSIONS_MATRIX.md (роли, матрица доступа, data scoping)
  - ENTITY_RELATIONSHIPS.md (#63, #67)
  - SCREEN_CATALOG.md (SCR-302)
validation_status: "confirmed (терминологические расхождения задокументированы)"
---

> **Канонический источник (ru).** Переводы создаются из этого файла после
> отдельного решения. При правках сначала меняем источник.

# Что такое роль

**Роль** (Role) — предопределённая модель доступа (RBAC). Роль определяет, какие
пункты меню, данные и действия доступны пользователю.

## Кратко

Роль — это «кем является» пользователь на платформе. От роли зависит, какие
разделы он видит и что может делать. Один и тот же экран разным ролям может
показывать разные данные.

## Что это такое

Платформа использует ролевую модель доступа. Продуктовых ролей — **восемь**
(плюс служебные). Их коды хранятся в
[Entity States → Коды ролей](../../ENTITY_STATES.md), а полная матрица
«роль → доступ» — в [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

**Роли платформы:** Client, Buyer, Storekeeper, Supervisor, Researcher, Admin,
Freelancer (в роутах/бэкенде — **Service Provider**).

> ⚠️ Терминологические расхождения (не нормализуем молча):
> - **Freelancer** (дизайн) = **Service Provider** (роуты/бэкенд).
> - **Storekeeper** в бэкенд-таблицах может встречаться как **warehouse**.

## Зачем это нужно

- Роль задаёт границы доступа для каждого пользователя.
- Роли обеспечивают, что одни и те же данные показываются по-разному в
  зависимости от того, кто их смотрит.
- На ролях строятся сквозные процессы платформы (ресёрч → проверка → закупка →
  склад).

## Основные атрибуты

- **Код роли** — числовой идентификатор (см. [Entity States](../../ENTITY_STATES.md)).
- **Набор доступов** — какие пункты меню и действия разрешены.
- **Права / пресеты** — уточняют доступ внутри роли.

## Жизненный цикл и статусы

Роль — это конфигурация доступа, а не процессная сущность; собственного
жизненного цикла со статусами у неё нет. Значения кодов ролей — в
[Entity States](../../ENTITY_STATES.md).

## Связи с другими сущностями

- Пользователь **имеет** роль.
- Роль **связана** с разрешениями (какие доступы она даёт).
- Пресеты прав уточняют доступ внутри роли.

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

Роль есть у каждого пользователя. Управляет ролями и правами преимущественно
**Admin** — см. [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-302](../../SCREEN_CATALOG.md) Права пользователей | Настройка ролей и доступов |

## Связанные сценарии

- **WF-060** — настройка прав пользователя / пресета (Admin).

## Термины и справочники

- Коды ролей: [Entity States](../../ENTITY_STATES.md).
- Матрица доступа: [Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Сколько ролей на платформе? | Восемь продуктовых ролей плюс служебные; коды — в Entity States. |
| Freelancer и Service Provider — разные роли? | Нет, это одна роль под двумя именами (дизайн ↔ бэкенд). |
| Почему один экран показывает разным ролям разное? | Данные фильтруются по роли и правам (data scoping). |

## Связанные статьи

- [007 — Пользователь](007-user.md)
- [009 — Право доступа](009-permission.md)
- [010 — Пресет прав](010-permission-preset.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md) и [PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md).
- [x] Метаданные — front matter полон.
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования справочников — коды/матрица даны ссылками.
- [x] Расхождения Freelancer↔Service Provider и Storekeeper↔warehouse зафиксированы, не нормализованы.
- [x] Внутренние ссылки корректны.
