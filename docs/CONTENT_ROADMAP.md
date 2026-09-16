# ASeller Knowledge Base — Content Roadmap

> Редакторская дорожная карта всех статей базы знаний Seller Exchange (внутр.
> **AmazonService / AS**): что запланировано, в черновике, на ревью и
> опубликовано. Рабочий язык — **RU** (RU-first, см.
> [LOCALIZATION_GUIDE](LOCALIZATION_GUIDE.md)).
>
> Это **не** информационная архитектура ([INFORMATION_ARCHITECTURE](INFORMATION_ARCHITECTURE.md))
> и **не** доменная модель ([DOMAIN_MODEL](DOMAIN_MODEL.md)) — это практический
> план выпуска контента.

---

## 1. Назначение

Документ отслеживает жизненный цикл каждой статьи (planned → template → draft →
review → approved → published) и связывает её с:

- **сущностями** ([DOMAIN_MODEL](DOMAIN_MODEL.md), [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md));
- **сценариями** ([WORKFLOW_CATALOG](WORKFLOW_CATALOG.md), `WF-###`);
- **экранами** ([SCREEN_CATALOG](SCREEN_CATALOG.md), `SCR-###`);
- **ролями** и **модулями** ([PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md));
- **типом статьи** и **статусом публикации**;
- **статусом локализации** (RU-источник → EN/UA/ZH).

Каждой статье присвоен идентификатор `ART-###`.

## 2. Принципы контента

- **RU-first**: источник пишем и утверждаем на русском; переводы — из финального RU.
- **Один факт — один источник**: поля → [GLOSSARY](GLOSSARY.md); статусы →
  [ENTITY_STATES](ENTITY_STATES.md); связи → [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md).
- **Concept ≠ Screen Guide ≠ Workflow Guide** — разные типы, разные задачи.
- **Не дублируем** Domain Model / Glossary / Entity Relationships — **ссылаемся**.
- У каждой статьи есть: **related entities**, **article type**, **status**.
- Статья **проходит ревью на RU** до начала локализации.

## 3. Типы статей

| Тип | Назначение |
|---|---|
| **Foundation** | Концепт-статья «что такое X» о ключевой сущности (Marketplace Academy, beginner). |
| **Glossary** | Короткое определение термина (живёт в [GLOSSARY](GLOSSARY.md); в roadmap — как отсылка). |
| **Marketplace Academy** | Обучающая статья о работе на Amazon (термины, практики, стратегии). |
| **User Guide** | Как пользователю выполнить задачу в продукте (пошагово). |
| **Screen Guide** | Справочник по конкретному экрану/модалке (элементы, действия, доступ). |
| **Workflow Guide** | Сквозной сценарий по ролям (end-to-end операция). |
| **FAQ** | Частые вопросы по теме/модулю. |
| **Troubleshooting** | Проблема → причина → решение. |
| **SEO / Pillar** | Крупная статья для органического трафика, связывает Academy и продукт. |
| **Release Notes** | Хроника изменений (патч-ноуты). |
| **Internal Reference** | Внутренний документ для команды (не публичный). |

## 4. Модель статусов

**Статус готовности:**
`planned` → `template` → `draft` → `review` → `approved` → `published`
+ поперечные: `needs validation`, `blocked`.

**Статус локализации:**
`ru-source` · `en-needed` · `en-ready` · `ua-needed` · `ua-ready` · `zh-needed` · `zh-ready`.
(в таблице сокращённо; `en-draft` = перевод создан, но не утверждён).

---

## 5. Главная дорожная карта

Колонки: ID · Title RU · Title EN · Type · Source Entity · Related Entities ·
Module · Roles · Related Workflows · Related Screens · Status · Localization · Notes.
Разбита на группы для читаемости; нумерация `ART-###` сквозная.

### 5.1 Foundation / Core Entities

| ID | Title RU | Title EN | Type | Source Entity | Related Entities | Module | Roles | Workflows | Screens | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ART-001 | Что такое товар | What is a Product | Foundation | Product | ASIN, Supplier Card, Order, Box | Inventory | Client, Buyer, Researcher, Supervisor, Admin | WF-001, WF-030 | SCR-120,121,124 | approved | ru-source · en-draft · ua/zh-needed | RU-источник утверждён; Product↔Inventory Item — NV |
| ART-002 | Что такое инвентарь | What is Inventory | Foundation | Inventory | Product, Report, Return | Inventory | Client, Admin | WF-030 | SCR-120,121,122 | approved | ru-source · en-draft · ua/zh-needed | RU-источник утверждён |
| ART-003 | Что такое заказ | What is an Order | Foundation | Order | Order Item, Product, Box, Supplier, Payment | Orders | Client, Buyer, Admin | WF-005,006,030,031 | SCR-100…104, M01 | approved | ru-source · en-draft · ua/zh-needed | RU-источник утверждён; Order Item — NV |
| ART-004 | Что такое коробка | What is a Box | Foundation | Box | Super Box, Order, Batch, Task, Tariff | Warehouse | Client, Storekeeper, Admin | WF-007,031,035 | SCR-200,202, M04,M05 | approved | ru-source · en-draft · ua/zh-needed | RU-источник утверждён; Super Box (не сущность) и Shipment — NV |
| ART-005 | Что такое партия | What is a Batch | Foundation | Batch | Box, Shipment | Batches | Client, Storekeeper, Admin | WF-035,041 | SCR-240,241,242 | draft · needs validation · blocked (DM8) | ru-source · en-needed | **Blocked до DM8** (жизненный цикл + Shipment) |
| ART-006 | Что такое магазин | What is a Store | Foundation | Store | Marketplace, Product, Parsing Report | Stores | Client | WF-034 | SCR-280,281 | approved | ru-source | RU-источник утверждён |
| ART-007 | Что такое пользователь | What is a User | Foundation | User | Account, Role, Sub-user | Users | все | WF-060 | SCR-016,017,300,301 | approved | ru-source | RU-источник утверждён; Account/User/Client — DM3 закрыт |
| ART-008 | Что такое роль | What is a Role | Foundation | Role | Permission, User | Access Control | все | WF-060 | SCR-302 | approved | ru-source | RU-источник утверждён; Freelancer=Service Provider, Storekeeper=warehouse |
| ART-009 | Что такое разрешение | What is a Permission | Foundation | Permission | Role, Permission Preset | Access Control | Admin, Buyer | WF-060 | SCR-302, M06 | approved | ru-source | RU-источник утверждён |
| ART-010 | Что такое пресет прав | Permission Preset | Foundation | Permission Preset | Permission, Sub-user | Access Control | Admin | WF-060 | SCR-302 | approved | ru-source | RU-источник утверждён; без lifecycle (DM10) |
| ART-011 | Что такое поставщик | What is a Supplier | Foundation | Supplier | Supplier Card, Product, Order | Suppliers | Buyer, Supervisor | WF-003,020 | SCR-190 | approved | ru-source | RU-источник утверждён; Supplier Card — ART-012 (планируется) |
| ART-012 | Карточка поставщика | Supplier Card | Foundation | Supplier Card | Supplier, Product, Idea | Suppliers, Exchange | Buyer, Supervisor, Client | WF-003,004 | SCR-161 | approved | ru-source | RU-источник утверждён; статусы — ENTITY_STATES |
| ART-013 | Карточка товара | Product Card | Foundation | Product Card | Product, ASIN, Idea | Product Research | Researcher, Supervisor, Buyer, Client | WF-001,002,004 | SCR-124,180,181 | approved | ru-source | RU-источник утверждён; Research Product↔Idea — NV (DM4) |
| ART-014 | Что такое идея | Product Idea | Foundation | Product Idea | Product, Supplier Search Request | Product Launch | Client, Buyer | WF-032 | SCR-140…146, M07 | approved | ru-source | RU-источник утверждён; статусы идеи — ENTITY_STATES |
| ART-015 | Заявка на услугу | Service Request | Foundation | Service Request | Proposal, Service | Freelance | Client, Freelancer | WF-033,050 | SCR-260,261,262 | approved | ru-source | RU-источник утверждён; kind MY/VACANT |
| ART-016 | Предложение | Proposal | Foundation | Proposal | Service Request, Service | Freelance | Freelancer, Client | WF-050 | SCR-263,264 | approved | ru-source | RU-источник утверждён |
| ART-017 | Что такое платёж | Payment | Foundation | Payment | Order, Supplier, Balance | Finance | Buyer, Client, Admin | WF-023 | SCR-012 | approved | ru-source | RU-источник утверждён; своих статусов нет — через статусы заказа |
| ART-018 | Что такое возврат | Return | Foundation | Return | Product, Order | Inventory, Logistics | Client | — | SCR-120 | approved | ru-source | RU-источник утверждён; Return↔Order — NV |
| ART-019 | Что такое уведомление | Notification | Foundation | Notification | Order, Box, Tariff | Notifications | Client, Buyer, Storekeeper, Freelancer, Admin | — | SCR-013 | approved | ru-source | RU-источник утверждён; статусов нет — вкладки по темам |
| ART-020 | Тикет поддержки | Support Ticket | Foundation | Support Ticket | User, Feedback | Support | все | WF-072 | SCR-015 | approved | ru-source | RU-источник утверждён; Feedback = ответ Admin/Mod (DM9) |
| ART-021 | Что такое отчёт | What is a Report | Foundation | Report | Product, Inventory, Campaign | Analytics | Client, Supervisor, Admin | — | SCR-122,281 | approved | ru-source | RU-источник утверждён; типы отчётов — DM19 (уточняется) |
| ART-022 | Что такое кампания | Campaign | Foundation | Campaign | Product, Report | Advertising | Client | — | SCR-120,122 | approved | ru-source | RU-источник утверждён |
| ART-023 | PPC-метрики | PPC Metrics | Foundation | PPC Metrics | Campaign, Product | Advertising | Client | — | SCR-120,122 | approved | ru-source | RU-источник утверждён; поля — GLOSSARY; ACoS/TACoS/ROAS — ART-042 |
| ART-024 | Voice of Customer | Voice of Customer | Foundation | Voice of Customer | Product, Return | Analytics | Client | — | — | planned · needs validation | ru-source | Срез (DM12); зависит от Return Badge |

### 5.2 Marketplace Academy

| ID | Title RU | Title EN | Type | Source Entity | Module | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|---|
| ART-025 | Термины маркетплейса | Marketplace Terms | Marketplace Academy | Marketplace | Stores | approved | ru-source | Hub-навигатор `academy/025`; Shipment/Connected App помечены NV |
| ART-026 | Что такое ASIN | ASIN | Marketplace Academy | ASIN | Product | approved | ru-source | Файл `articles/academy/026-asin.md`; RU-источник утверждён |
| ART-027 | Что такое SKU | SKU | Marketplace Academy | Product (attr) | Product | approved | ru-source | Файл `academy/027-sku.md`; SKU — атрибут (DM13) |
| ART-028 | ASIN vs SKU vs FNSKU | ASIN vs SKU vs FNSKU | Marketplace Academy | ASIN, FNSKU | Product | approved | ru-source | Файл `academy/028-asin-vs-sku-vs-fnsku.md`; сравнительная |
| ART-029 | Что такое FBA | FBA | Marketplace Academy | — | Warehouse | approved | ru-source | Файл `academy/029-fba.md`; термин Amazon |
| ART-030 | Что такое FBM | FBM | Marketplace Academy | — | Orders | approved | ru-source | Файл `academy/030-fbm.md`; термин Amazon |
| ART-031 | Что такое MOQ | MOQ | Marketplace Academy | Supplier | Suppliers | approved | ru-source | Файл `academy/031-moq.md`; мин. партия |
| ART-032 | Что такое бренд | Brand | Marketplace Academy | Brand | Product | approved | ru-source | Файл `academy/032-brand.md`; Brand ≠ Brand Launch (DM17) |
| ART-033 | Что такое категория | Category | Marketplace Academy | Category | Product | approved | ru-source | Файл `academy/033-category.md` |
| ART-034 | Что такое вариация | Variation | Marketplace Academy | Variation | Product | approved | ru-source | Файл `academy/034-variation.md`; Variation = Product (DM18) |
| ART-035 | Баркод / UPC / EAN | Barcode / UPC / EAN | Marketplace Academy | Barcode | Product | approved | ru-source | Файл `academy/035-barcode-upc-ean.md`; UPC/EAN — атрибуты (DM13) |
| ART-036 | Amazon SP-API | Amazon SP-API | Marketplace Academy | Integration | Integrations | approved | ru-source | Файл `academy/036-amazon-sp-api.md`; Connected App — NV (DM6) |
| ART-037 | Прогноз запасов | Inventory Forecasting | Marketplace Academy | Inventory | Inventory | approved | ru-source | Файл `academy/037-inventory-forecasting.md`; Days of Supply |
| ART-038 | Out of Stock | Out of Stock | Marketplace Academy | Inventory | Inventory | approved | ru-source | Файл `academy/038-out-of-stock.md` |
| ART-039 | Дозакупка (Restock) | Restock | Marketplace Academy | Inventory, Order | Inventory | approved | ru-source | Файл `academy/039-restock.md` |
| ART-040 | Buy Box | Buy Box | Marketplace Academy | Product | Analytics | approved | ru-source | Файл `academy/040-buy-box.md`; Featuredoffer Price / Sold By |
| ART-041 | Основы PPC | PPC Basics | Marketplace Academy | Campaign | Advertising | approved | ru-source | Файл `academy/041-ppc-basics.md` |
| ART-042 | ACoS / TACoS / ROAS | ACoS / TACoS / ROAS | Marketplace Academy | PPC Metrics | Advertising | approved | ru-source | Файл `academy/042-acos-tacos-roas.md`; ROAS — отраслевая метрика |
| ART-043 | Юнит-экономика | Unit Economics | Marketplace Academy | Product | Finance | approved | ru-source | Файл `academy/043-unit-economics.md`; ROI, Margin, COG |
| ART-044 | Private Label vs Wholesale | Private Label vs Wholesale | Marketplace Academy | Strategy | Product Research | approved | ru-source | Файл `academy/044-private-label-vs-wholesale.md`; стратегии (ENTITY_STATES) |

### 5.3 User Guide

| ID | Title RU | Title EN | Type | Related Entities | Module | Roles | Workflows | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| ART-045 | С чего начать | Getting Started | User Guide | User, Account | Onboarding | все | WF-070 | approved | ru-source | `user-guide/045-…md`; входная точка |
| ART-046 | Первый вход | First Login | User Guide | User | Auth | все | WF-070 | approved | ru-source | `user-guide/046-…md` |
| ART-047 | Подключить магазин Amazon | Connect Amazon Store | User Guide | Store, Integration | Stores | Client | WF-034 | approved | ru-source | `user-guide/047-…md` |
| ART-048 | Настроить команду | Set up team | User Guide | Sub-user, Permission Preset | Users | Client, Admin | WF-060 | approved | ru-source | `user-guide/048-…md` |
| ART-049 | Создать первый товар | Create first product | User Guide | Product | Inventory | Client | WF-030 | approved | ru-source | `user-guide/049-…md` |
| ART-050 | Создать первый заказ | Create first order | User Guide | Order, Box | Orders | Client | WF-030,031 | approved | ru-source | `user-guide/050-…md` |
| ART-051 | Работа с инвентарём | Use Inventory | User Guide | Inventory, Product | Inventory | Client | WF-030 | approved | ru-source | `user-guide/051-…md` |
| ART-052 | Управление коробками | Manage Boxes | User Guide | Box, Super Box | Warehouse | Client, Storekeeper | WF-007,035 | approved | ru-source | `user-guide/052-…md` |
| ART-053 | Создать партию | Create Batch | User Guide | Batch, Box | Batches | Client, Storekeeper | WF-035,041 | blocked | ru-source | `user-guide/053-…md` (шаблон BLOCKED, DM8) |
| ART-054 | Пользователи и права | Manage Users and Permissions | User Guide | User, Permission Preset | Users | Admin, Client | WF-060 | approved | ru-source | `user-guide/054-…md` |
| ART-055 | Настроить уведомления | Configure Notifications | User Guide | Notification | Notifications | Client | — | approved | ru-source | `user-guide/055-…md` |
| ART-056 | Как пользоваться поддержкой | Use Support | User Guide | Support Ticket | Support | все | WF-072 | approved | ru-source | `user-guide/056-…md` |

### 5.4 Screen Guides

| ID | Title RU | Title EN | Type | Screen | Module | Roles | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|---|---|
| ART-057 | Инвентарь — товары | Inventory Products | Screen Guide | SCR-120 | Inventory | Client, Admin | approved | ru-source · en-needed | `articles/screens/inventory-products.md`; RU-источник утверждён |
| ART-058 | Детали товара | Product Detail | Screen Guide | SCR-121 | Inventory | Client, Admin | approved | ru-source | `screens/product-detail.md`; mhtml ProductView (контекст биржи) |
| ART-059 | Список заказов | Orders List | Screen Guide | SCR-100,103 | Orders | Client, Buyer | approved | ru-source | `screens/orders-list.md`; mhtml Myorders/OrdersBuyer |
| ART-060 | Модалка создания заказа | Create Order Modal | Screen Guide | SCR-M01 | Orders | Client | approved | ru-source | `screens/create-order-modal.md`; mhtml CreateOrderModal |
| ART-061 | Склад — коробки на складе | Warehouse In Stock | Screen Guide | SCR-200 | Warehouse | Client | approved | ru-source | `screens/warehouse-in-stock.md`; mhtml Warehouse-Boxes |
| ART-062 | Мой склад | My Warehouse | Screen Guide | SCR-202 | Warehouse | Storekeeper | approved | ru-source | `screens/my-warehouse.md`; mhtml Storekeeper.Warehouse (Dark/En) |
| ART-063 | Партии — ожидающие отправки | Batches Awaiting Send | Screen Guide | SCR-240 | Batches | Client, Storekeeper | blocked | ru-source | Зависит от DM8 |
| ART-064 | Партии — отправленные | Batches Sent | Screen Guide | SCR-241 | Batches | Client, Storekeeper, Admin | approved | ru-source | `screens/batches-sent.md`; mhtml BatchesSent; lifecycle партии — NV (DM8) |
| ART-065 | Пользователи | Users | Screen Guide | SCR-016,300,301 | Users | все | approved | ru-source | `screens/users.md`; mhtml Client-Users/AnotherUserProfile |
| ART-066 | Права пользователей | Permissions | Screen Guide | SCR-302, M06 | Access Control | Admin, Buyer | approved | ru-source | `screens/permissions.md`; mhtml Admin.UsersPermissions |
| ART-067 | Уведомления | Notifications | Screen Guide | SCR-013 | Notifications | Client, Buyer, Storekeeper, Freelancer, Admin | approved | ru-source | `screens/notifications.md`; mhtml Client-Notifications-* |
| ART-068 | Сообщения | Messages | Screen Guide | SCR-014 | Collaboration | все кроме Researcher | approved | ru-source | `screens/messages.md`; mhtml Client-Messages |
| ART-069 | Поддержка | Support | Screen Guide | SCR-015 | Support | все | approved | ru-source | `screens/support.md`; mhtml Client-Support (Dark/En) |

### 5.5 Workflow Guides

| ID | Title RU | Title EN | Type | Workflow | Roles | Entities | Screens | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| ART-070 | Ресёрчер создаёт карточку товара | Researcher creates product card | Workflow Guide | WF-001 | Researcher | Product Card | SCR-123,124 | approved | ru-source | `workflows/070-…md` |
| ART-071 | Супервайзер проверяет карточку | Supervisor checks product card | Workflow Guide | WF-002 | Supervisor | Product Card | SCR-180,181 | approved | ru-source | `workflows/071-…md` |
| ART-072 | Байер ищет поставщика | Buyer searches supplier | Workflow Guide | WF-003 | Buyer | Supplier, Supplier Search Request | SCR-191,192 | approved | ru-source | `workflows/072-…md` |
| ART-073 | Клиент создаёт заказ из инвентаря | Client creates order from Inventory | Workflow Guide | WF-030 | Client | Order, Product, Box | SCR-120, M01 | approved | ru-source | `workflows/073-…md` |
| ART-074 | Байер обрабатывает заказ | Buyer processes order | Workflow Guide | WF-006 | Buyer | Order, Payment | SCR-103,104 | approved | ru-source | `workflows/074-…md` |
| ART-075 | Сторкипер принимает коробки | Storekeeper receives boxes | Workflow Guide | WF-007 | Storekeeper | Box, Warehouse Task | SCR-202, M04 | approved | ru-source | `workflows/075-…md` |
| ART-076 | Клиент отправляет коробки в партию | Client sends boxes into batch | Workflow Guide | WF-035 | Client | Box, Batch | SCR-200,240 | blocked | ru-source | `workflows/076-…md` (шаблон BLOCKED, DM8) |
| ART-077 | Сторкипер формирует партию | Storekeeper forms batch | Workflow Guide | WF-041 | Storekeeper | Batch, Box | SCR-240,241 | blocked | ru-source | `workflows/077-…md` (шаблон BLOCKED, DM8) |
| ART-078 | Админ управляет правами | Admin manages permissions | Workflow Guide | WF-060 | Admin, Buyer | Permission Preset, Sub-user | SCR-302, M06 | approved | ru-source | `workflows/078-…md` |
| ART-079 | Пользователь создаёт тикет | User creates support ticket | Workflow Guide | WF-072 | все | Support Ticket | SCR-015 | approved | ru-source | `workflows/079-…md` |

### 5.6 SEO / Pillar

| ID | Title RU | Title EN | Type | Module | Status | Localization | Notes |
|---|---|---|---|---|---|---|---|
| ART-080 | Что такое Seller Exchange? | What is Seller Exchange? | SEO / Pillar | — | approved | ru-source | `pillar/080-…md`; SEO-ревью перед публикацией |
| ART-081 | Полный гайд по построению Amazon-бизнеса | Complete Guide to Building an Amazon Business | SEO / Pillar | — | approved | ru-source | `pillar/081-…md`; связан с Workflow Guides |
| ART-082 | Автоматизация маркетплейса | Marketplace Automation | SEO / Pillar | — | approved | ru-source | `pillar/082-…md`; Connected App — NV (DM6) |
| ART-083 | Как управлять запасами на Amazon | How to Manage Amazon Inventory | SEO / Pillar | Inventory | approved | ru-source | `pillar/083-…md` |
| ART-084 | Как избежать out of stock | How to Prevent Out of Stock | SEO / Pillar | Inventory | approved | ru-source | `pillar/084-…md` |
| ART-085 | Как организовать команду Amazon-продавца | How to Organize an Amazon Seller Team | SEO / Pillar | Users | approved | ru-source | `pillar/085-…md` |
| ART-086 | Единое рабочее пространство для операций | One Workspace for Marketplace Operations | SEO / Pillar | — | approved | ru-source | `pillar/086-…md` |

### 5.7 Редакторская статистика (обновлено 2026-07-02)

| Статус | Кол-во | Статьи |
|---|---|---|
| **approved** | 80 | все ART, кроме blocked и ART-024 |
| **review** | 0 | — |
| **draft** | 0 | — |
| **blocked** | 5 | ART-005, ART-053, ART-063, ART-076, ART-077 |
| **planned** | 1 | ART-024 (Voice of Customer, needs validation — DM12) |
| **Всего** | **86** | — |

Поперечная пометка **needs validation** — 2 статьи: ART-005, ART-024
(ART-025 — `approved` с флагами *Needs validation* по Shipment/Connected App).
Примечания: ART-005 — составной статус (`draft · needs validation · blocked`),
учтён как **blocked**. ART-013/018/021 — `approved` с пометками *Needs validation*
(Research Product↔Idea DM4; Return↔Order; набор отчётов DM19) — на статус не влияют.
Раскладка approved: Foundation 22 (ART-001–004, 006–023 кроме 005) · Academy 20
(ART-025–044) · Screen Guide 12 (ART-057–069 кроме 063) · Workflow Guide 8
(ART-070–079 кроме 076, 077) · SEO/Pillar 7 (ART-080–086) · User Guide 11
(ART-045–056 кроме 053).

---

## 6. Приоритетные волны

Прогресс измеряется по `approved`-статьям (10 делений). Обновлено 2026-07-02.

### Волна 1 — Core Entities — В работе
**Цель:** объяснить базовые понятия платформы.

Ключевая веха — 5 core-entity статей (Product, Inventory, Order, Box, Batch):
```
████████░░  4 / 5   80%   (остаётся ART-005, blocked — DM8)
```

Вся Foundation-волна (ART-001…024, 24 статьи):
```
█████████▎  22 / 24   92%
```
Готово (`approved`): ART-001–004, ART-006–023 (кроме 005).
В работе/заблокировано: ART-005 (blocked — DM8).
Осталось: **ART-024** (Voice of Customer — `needs validation`, DM12).

### Волна 2 — Marketplace Terms — Завершена ✅
```
██████████  20 / 20   100%   (approved 025–044)
```
**Цель:** собрать поисковый глоссарий и базу Academy. ART-025…044 — готово: hub
[Термины маркетплейса](articles/academy/025-marketplace-terms.md) +
19 терминов (ASIN…Private Label vs Wholesale). В hub помечены *Needs validation*
Shipment и Connected App (флагами, не утверждениями).

### Волна 3 — Screen Guides — Почти завершена
```
█████████▍  12 / 13   92%   (approved: 057–069 кроме 063)
```
**Цель:** задокументировать реальный UI. ART-057…069. Визуальные источники —
mhtml из `figma-mcp/sources/mhtml/`.
Осталось: **ART-063** Batches Awaiting (**blocked DM8**) — единственная незакрытая.

### Волна 4 — Workflow Guides — Почти завершена
```
████████░░  8 / 10   80%   (approved: 070–075, 078, 079)
```
**Цель:** объяснить сквозные операции. ART-070…079. Папка `articles/workflows/`.
Готово 8: карточка (070), проверка супервайзером (071), поиск поставщика (072),
заказ из инвентаря (073), обработка заказа (074), приёмка коробок (075), права
(078), тикет (079).
Осталось: **ART-076** (Client sends boxes into batch) и **ART-077** (Storekeeper
forms batch) — **blocked DM8** (созданы шаблоны BLOCKED с причиной и вопросами).

### Волна 5 — Pillar / SEO — Завершена ✅
```
██████████  7 / 7   100%   (approved: 080–086)
```
**Цель:** органический трафик и связка Academy ↔ продукт. ART-080…086 — готово
(папка `articles/pillar/`). Все — RU-источник; перед публикацией нужен
**SEO/маркетинг-ревью** (помечено в чеклистах).

### Волна 6 — Локализация — Not started (отложена)
```
░░░░░░░░░░  0%
```
**Цель:** перевести утверждённые RU-источники на EN, UA, ZH. Вне текущего этапа —
проект остаётся RU-source only. Начнётся с ART-001…004 после отдельного решения.

### Рекомендуемые следующие статьи

Marketplace Terms ✅ завершена. Идёт Волна 3 (Screen Guides) — есть mhtml-захваты
в `figma-mcp/sources/mhtml/`. Batch-связанные работы **не рекомендуются** до **DM8**.

| Приоритет | ID | Статья | mhtml-захват |
|---|---|---|---|
| 1 | ART-061 | Warehouse In Stock (Screen Guide) | `Client-Boxesinstock`, `Client-Warehouse-Boxes-*` |
| 2 | ART-062 | My Warehouse (Screen Guide) | `Storekeeper.Warehouse` |
| 3 | ART-065 | Users (Screen Guide) | `Client-Users`, `Client.Users.*` |
| 4 | ART-066 | Permissions (Screen Guide) | `Admin.UsersPermissions*` |
| 5 | ART-067 | Notifications (Screen Guide) | `Client-Notifications-*` |
| 6 | ART-068 | Messages (Screen Guide) | `Client-Messages` |
| 7 | ART-069 | Support (Screen Guide) | `Client-Support` |
| 8 | ART-073 | Клиент создаёт заказ из инвентаря (Workflow Guide) | — |

Исключены (blocked до DM8): ART-005, ART-053, ART-063 (Batches Awaiting),
ART-076, ART-077. ART-024 (Voice of Customer) — `needs validation` (DM12).
ART-024 (Voice of Customer) — `needs validation`, писать после уточнения DM12.

## 7. Зависимости (правила очерёдности)

- **Не писать Workflow Guide** раньше соответствующих Foundation-статей.
- **Не писать Screen Guide** раньше, чем экран стабилизирован.
- **Не локализовать** статью до её `approved` на RU.
- **Не писать Pillar/SEO** раньше, чем существуют базовые термины глоссария.
- **Не финализировать статью про партию (ART-005)** до закрытия **DM8**
  (жизненный цикл Batch).
- **Не финализировать статьи, связанные с Shipment**, пока не подтверждено,
  сущность это или жизненный цикл коробки.

## 8. Маппинг на Framer CMS

Поля коллекции статей ↔ front matter ([ARTICLE_TEMPLATE](ARTICLE_TEMPLATE.md)):

| Framer поле | Источник в roadmap / front matter |
|---|---|
| `title` | Title RU (источник) / Title EN (перевод) |
| `slug` | `slug` |
| `article_type` | Type |
| `section` | `section` (Marketplace Academy / User Guide / …) |
| `status` | Status (planned…published) |
| `locale` | ru / en / ua / zh |
| `roles` | Roles |
| `modules` | Module |
| `entities` | Source Entity + Related Entities |
| `workflows` | Related Workflows (`WF-###`) |
| `screens` | Related Screens (`SCR-###`) |
| `related_articles` | связи `ART-###` |
| `seo_title` / `seo_description` | из front matter статьи |

Дополнительно для управления: `validation_status`, `localization_status`,
`series` («Foundations / Core Entities»).

## 9. Открытые редакторские вопросы

- Должна ли публичная Marketplace Academy стать EN-first позже, тогда как
  внутренний источник остаётся RU-first?
- Какие статьи публиковать на seller.exchange в первую очередь?
- Какие статьи оставить только внутренними (Internal Reference)?
- Каким Screen Guides нужны свежие скриншоты (без реальных ПДн)?
- Какова частота публикаций (cadence)?
- Кто проверяет продуктовую точность (product accuracy reviewer)?
- Кто владеет локализацией (ответственный за EN/UA/ZH)?

---

## Легенда

- **Статусы:** planned · template · draft · review · approved · published ·
  needs validation · blocked.
- **Локализация:** ru-source · en-needed/en-draft/en-ready · ua-needed/ua-ready ·
  zh-needed/zh-ready.
- Открытые вопросы по сущностям — в [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md).
