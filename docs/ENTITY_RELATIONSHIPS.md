# Entity Relationships — Seller Exchange

> Каталог бизнес-связей между подтверждёнными сущностями платформы Seller
> Exchange (внутр. **AmazonService / AS**). Дополняет
> [DOMAIN_MODEL](DOMAIN_MODEL.md) (сущности — там, связи — здесь; держим синхронно).
>
> **Это НЕ** схема БД, **НЕ** ERD. Это семантический каталог связей для
> Knowledge Base, Marketplace Academy, Framer CMS, AI-ассистента, поиска,
> product/UX и обсуждений с backend.
>
> **Принцип:** точность важнее полноты. Связи не выдумываются. Если связь лишь
> подразумевается, но не подтверждена документацией — `Relationship = ?`,
> `Cardinality = ?`, `Status = Needs validation`.
>
> Актуализировано 2026-07-01 по ответам DM1–DM19
> ([DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md)).

---

## 1. Relationship Types

Разрешённые бизнес-глаголы связей (без технических терминов вроде foreign key):

| Глагол | Смысл |
|---|---|
| has | обладает атрибутом/подчинённой сущностью |
| belongs to | принадлежит родителю |
| contains | содержит внутри |
| groups | группирует |
| references | ссылается на |
| creates | порождает |
| owns | владеет |
| uses | использует |
| generated from | производится из |
| published on | публикуется на |
| assigned to | назначается на |
| attached to | крепится к |
| processed by | обрабатывается |
| stored in | хранится в |
| managed by | управляется |
| configured by | настраивается |
| tagged with | размечается |
| packed into | упаковывается в |
| goes through | проходит через |
| answers | отвечает на |
| extends | расширяет |
| connected to | подключается к |
| exchanged between | обменивается между |
| = | тождественна (одна и та же сущность) |

---

## 2. Entity Relationship Table

Cardinality: `1:1`, `1:N`, `N:1`, `N:N`, `?` (не подтверждена). Status:
`Confirmed` / `Needs validation`. Evidence: DOMAIN_MODEL, WORKFLOW_CATALOG,
SCREEN_CATALOG, ENTITY_STATES, PERMISSIONS_MATRIX, GLOSSARY, ROUTES
(`platform-routes.md`), DATA_FILTERS (`docs/Data filters*.md`), DM# (ответы
техлида, см. [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md)).

| # | Source | Relationship | Target | Cardinality | Status | Evidence | Notes |
|---|---|---|---|---|---|---|---|
| 1 | Product | has | ASIN | 1:N | Confirmed | DOMAIN_MODEL, GLOSSARY | Вариации → неск. ASIN |
| 2 | Product | has | FNSKU | ? | Confirmed | GLOSSARY | Код FBA |
| 3 | Product | has | Barcode | ? | Confirmed | GLOSSARY | UPC/EAN/FNSKU (UPC/EAN — атрибуты, DM13) |
| 4 | Product | belongs to | Brand | N:1 | Confirmed | DOMAIN_MODEL, GLOSSARY | Один бренд у товара |
| 5 | Product | belongs to | Category | N:1 | Confirmed | DOMAIN_MODEL, GLOSSARY | Иерархия категорий не описана |
| 6 | Product | tagged with | Tag | N:N | Confirmed | GLOSSARY | Теги множественные |
| 7 | Product | has | Transparency Code | ? | Confirmed | GLOSSARY | Опциональный признак |
| 8 | Product | has | Variation | 1:N | Confirmed | DOMAIN_MODEL, DM18 | Variation — это Product |
| 9 | Variation | belongs to | Parent Product | N:1 | Confirmed | DOMAIN_MODEL, DM18 | Parent = связь/зависимость товаров |
| 10 | Product | appears in | Inventory | ? | Confirmed | DOMAIN_MODEL | Товар — строка инвентаря |
| 11 | Product | = | Inventory Item | 1:1 | Confirmed | DOMAIN_MODEL, DM2 | Одна сущность: карточка товара пользователя |
| 12 | Product | has | Supplier Card | 1:N | Confirmed | DOMAIN_MODEL, ROUTES | `currentSupplierCard`; статус связи = «Inventory item status» |
| 13 | Product | references | Supplier | N:N | Confirmed | DOMAIN_MODEL | Через Supplier Card |
| 14 | Product | has | Strategy | N:1 | Confirmed | GLOSSARY, ENTITY_STATES | Поле «Стратегия» |
| 15 | Product | packed into | Box | ? | Confirmed | DOMAIN_MODEL, WORKFLOW_CATALOG | Вероятно N:N |
| 16 | Product Card | references | Product | ? | Confirmed | DOMAIN_MODEL | 1:1 vs N:1 неясно |
| 17 | Product Card | processed by | Supervisor | N:1 | Confirmed | WORKFLOW_CATALOG, ENTITY_STATES | `checkedById` |
| 18 | Product Card | created by | Researcher | N:1 | Confirmed | WORKFLOW_CATALOG, ROUTES | `createdById` |
| 19 | Product Card | generated from | Idea | ? | Confirmed | DOMAIN_MODEL, ENTITY_STATES | Статус «Card creating» |
| 20 | Product Card | published on | Product Exchange | ? | Confirmed | WORKFLOW_CATALOG | Публикация на бирже |
| 21 | Idea | references | Product | ? | Confirmed | DATA_FILTERS | `parentProduct` |
| 22 | Idea | creates | Supplier Search Request | ? | Confirmed | DOMAIN_MODEL, DM7 | Мульти-ролевой процесс |
| 23 | Idea | has | Milestone | ? | Confirmed | DOMAIN_MODEL, DM11 | Вехи в Product Launch |
| 24 | Supplier | has | Supplier Card | 1:N | Confirmed | DOMAIN_MODEL, ROUTES | `v2/suppliers/*/cards` |
| 25 | Supplier Card | references | Product | N:N | Confirmed | ROUTES | `linked_products` |
| 26 | Supplier | participates in | Order | ? | Confirmed | WORKFLOW_CATALOG | Оплата поставщику |
| 27 | Supplier Search Request | assigned to | Buyer | ? | Confirmed | DOMAIN_MODEL, DM7 | Client сам или через Buyer |
| 28 | Order | created by | Client | N:1 | Confirmed | PERMISSIONS_MATRIX, WORKFLOW_CATALOG | `createdById` |
| 29 | Order | processed by | Buyer | N:1 | Confirmed | PERMISSIONS_MATRIX, WORKFLOW_CATALOG | `buyerId` |
| 30 | Order | contains | Order Item | 1:N | Confirmed | DOMAIN_MODEL, DM1 | Позиции заказа |
| 31 | Order Item | references | Product | ? | Confirmed | DOMAIN_MODEL, DM1 | Order Item — связка сущностей |
| 32 | Order | creates | Box | 1:N | Confirmed | WORKFLOW_CATALOG, SCREEN_CATALOG | Коробки по заказу |
| 33 | Order | references | Supplier | ? | Confirmed | WORKFLOW_CATALOG | Заказ у поставщика |
| 34 | Order | references | Payment | ? | Confirmed | WORKFLOW_CATALOG | Оплата поставщику |
| 35 | Order | has | Order Type | N:1 | Confirmed | ENTITY_STATES | LONG/STANDARD/URGENT/PROBLEMATIC |
| 36 | Box | contains | Product | ? | Confirmed | DOMAIN_MODEL | Вероятно N:N |
| 37 | Box | belongs to | Order | N:1 | Confirmed | WORKFLOW_CATALOG | Коробка по заказу |
| 38 | Box | processed by | Warehouse Task | ? | Confirmed | ENTITY_STATES, DOMAIN_MODEL | receive/edit/split/merge |
| 39 | Box | belongs to | Batch | N:1 | Confirmed | DOMAIN_MODEL | — |
| 40 | Box | belongs to | Super Box | N:1 | Confirmed | DOMAIN_MODEL, DM14 | Контейнер SB |
| 41 | Box | references | Destination | N:1 | Confirmed | DOMAIN_MODEL | `boxes.destination` |
| 42 | Box | references | Tariff | N:1 | Confirmed | DOMAIN_MODEL | `logicsTariff` |
| 43 | Box | stored in | Warehouse | N:1 | Confirmed | DOMAIN_MODEL | China/USA/AWD |
| 44 | Box | goes through | Shipment | ? | Needs validation | ENTITY_STATES | Shipment как сущность — NV (это статусы коробки) |
| 45 | Super Box | groups | Box | 1:N | Confirmed | DOMAIN_MODEL, DM14 | Контейнер из коробок (SB) |
| 46 | Batch | groups | Box | 1:N | Confirmed | DOMAIN_MODEL | — |
| 47 | Batch | sent as | Shipment | ? | Needs validation | DOMAIN_MODEL | Shipment entity NV; коды batch — DM8 позже |
| 48 | Warehouse | stores | Box | 1:N | Confirmed | DOMAIN_MODEL | China/USA/AWD |
| 49 | Warehouse | processes | Warehouse Task | ? | Confirmed | DOMAIN_MODEL | — |
| 50 | Warehouse | prepares | Batch | ? | Confirmed | DOMAIN_MODEL | — |
| 51 | Warehouse | managed by | Storekeeper | ? | Confirmed | PERMISSIONS_MATRIX | `storekeeperId` |
| 52 | Warehouse Task | assigned to | Storekeeper | N:1 | Confirmed | ROUTES, PERMISSIONS_MATRIX | `storekeeperId` |
| 53 | Warehouse Task | processes | Box | ? | Confirmed | ENTITY_STATES | — |
| 54 | Service Request | created by | Client | N:1 | Confirmed | ROUTES, WORKFLOW_CATALOG | `createdById` |
| 55 | Service Request | receives | Proposal | 1:N | Confirmed | DOMAIN_MODEL, ROUTES | Много предложений |
| 56 | Service Request | references | Service | ? | Confirmed | DOMAIN_MODEL | — |
| 57 | Service Request | has | Milestone | ? | Confirmed | DOMAIN_MODEL, DM11 | Вехи в Service Provider |
| 58 | Proposal | created by | Freelancer | N:1 | Confirmed | ROUTES | `createdById` |
| 59 | Service | created by | Freelancer | N:1 | Confirmed | ROUTES | `my-services` |
| 60 | Announcement | references | Service | ? | Confirmed | DOMAIN_MODEL, DM16 | Карточка услуги |
| 61 | Announcement | created by | Freelancer | N:1 | Confirmed | DOMAIN_MODEL, DM16 | Объявление Service Provider |
| 62 | User | has | Account | ? | Confirmed | DOMAIN_MODEL, DM3 | Account = учётка пользователя |
| 63 | User | has | Role | N:1 | Confirmed | PERMISSIONS_MATRIX | RBAC |
| 64 | User | has | Sub-user | 1:N | Confirmed | ROUTES, DOMAIN_MODEL | `masterUser`; у любой роли |
| 65 | Sub-user | assigned to | Permission Preset | ? | Confirmed | DOMAIN_MODEL | — |
| 66 | Permission Preset | contains | Permission | 1:N | Confirmed | DOMAIN_MODEL, DM10 | Набор без lifecycle |
| 67 | Role | has | Permission | N:N | Confirmed | PERMISSIONS_MATRIX | Матрица меню→роль |
| 68 | Sub-user | references | Product | N:N | Confirmed | PERMISSIONS_MATRIX, DATA_FILTERS | Разрешённые продукты |
| 69 | Sub-user | references | Store | N:N | Confirmed | PERMISSIONS_MATRIX, DATA_FILTERS | `shopIds` |
| 70 | Account | owns | Store | N:1 | Confirmed | DOMAIN_MODEL, DM3 | `shops.ownerId` |
| 71 | Account | owns | Product | 1:N | Confirmed | DATA_FILTERS, PERMISSIONS_MATRIX | `clientId` |
| 72 | Account | owns | Order | 1:N | Confirmed | PERMISSIONS_MATRIX | `createdById` |
| 73 | Store | references | Marketplace | N:1 | Confirmed | DOMAIN_MODEL | — |
| 74 | Marketplace | has | Store | 1:N | Confirmed | DOMAIN_MODEL | Обратная к #73 |
| 75 | Store | generates | Parsing Report | 1:N | Confirmed | SCREEN_CATALOG, ROUTES | `parsing-reports` |
| 76 | Niche | published on | Product Exchange | ? | Confirmed | SCREEN_CATALOG | Раздел биржи |
| 77 | Inventory | contains | Product | 1:N | Confirmed | DOMAIN_MODEL | Обратная к #10 |
| 78 | Return | references | Product | ? | Confirmed | GLOSSARY | Поле Returns |
| 79 | Return | references | Order | ? | Needs validation | DOMAIN_MODEL | Связь возврат↔заказ не описана |
| 80 | Listing | generated from | Product | ? | Confirmed | DOMAIN_MODEL, DM5 | Listing = набор отчётов |
| 81 | Payment | references | Supplier | ? | Confirmed | WORKFLOW_CATALOG | Оплата поставщику |
| 82 | Payment | references | User | N:1 | Confirmed | DATA_FILTERS | `recipient_id` |
| 83 | Report | generated from | Product | ? | Confirmed | DATA_FILTERS | Отчёты над товарами |
| 84 | Report | generated from | Inventory | ? | Confirmed | DOMAIN_MODEL | — |
| 85 | AI Tool | uses | Inventory | ? | Confirmed | DOMAIN_MODEL | Анализ по фильтрам |
| 86 | Campaign | references | Product | ? | Confirmed | GLOSSARY | PPC-метрики по товару |
| 87 | Dashboard | uses | Report | ? | Needs validation | DOMAIN_MODEL | Состав/виджеты NV (DM15) |
| 88 | Voice of Customer | references | Product | ? | Confirmed | DOMAIN_MODEL, DM12 | Срез возвратов |
| 89 | Voice of Customer | references | Return | ? | Confirmed | DOMAIN_MODEL, DM12 | `concession_rate`, `badge_status` |
| 90 | Notification | references | Order | ? | Confirmed | ROUTES, SCREEN_CATALOG | `orders-notification` |
| 91 | Notification | references | Box | ? | Confirmed | ROUTES | `boxes-notification` |
| 92 | Notification | references | Tariff | ? | Confirmed | ROUTES | `boxes-tariff-notification` |
| 93 | Message | exchanged between | User | N:N | Confirmed | SCREEN_CATALOG | Чат |
| 94 | Support Ticket | created by | User | N:1 | Confirmed | SCREEN_CATALOG, DM9 | Запрос пользователя |
| 95 | Feedback | answers | Support Ticket | N:1 | Confirmed | DOMAIN_MODEL, DM9 | Ответ поддержки |
| 96 | Feedback | created by | Admin/Moderator | N:1 | Confirmed | DOMAIN_MODEL, DM9 | — |
| 97 | Tariff | configured by | Storekeeper | N:1 | Confirmed | WORKFLOW_CATALOG | WF-042 |
| 98 | Destination | configured by | Storekeeper | ? | Confirmed | DOMAIN_MODEL | Также Admin |
| 99 | Milestone | attached to | Service Request | ? | Confirmed | DOMAIN_MODEL, DM11 | Раздел Service Provider |
| 100 | Milestone | attached to | Idea | ? | Confirmed | DOMAIN_MODEL, DM11 | Раздел Product Launch |
| 101 | Tour | assigned to | Role | ? | Confirmed | DATA_FILTERS | `role=user.role OR -1` |
| 102 | Parser | has | Parsing Profile | 1:N | Confirmed | ROUTES | `parsing/profiles` |
| 103 | Parser | has | Parsing Request | 1:N | Confirmed | ROUTES | `parsing/requests` |
| 104 | Dynamic Column | extends | Product | ? | Confirmed | DATA_FILTERS | `DYNAMIC_COLUMNS` wildcard |
| 105 | Integration | connected to | Store | ? | Confirmed | DATA_FILTERS | Amazon SP / SellerBoard |

---

## 3. Relationship Graph by Domain

Только подтверждённые связи; помеченные `[NV]` требуют валидации.

### Product
```
Product
 → has → ASIN / FNSKU / Barcode / Transparency Code / Strategy
 → belongs to → Brand
 → belongs to → Category
 → tagged with → Tag
 → has → Variation            (Variation → belongs to → Parent Product)
 → = → Inventory Item          (одна сущность, DM2)
 → has → Supplier Card
 → references → Supplier
 → appears in → Inventory
 → packed into → Box
```

### Product Research
```
Product Card
 → references → Product
 → processed by → Supervisor
 → created by → Researcher
 → generated from → Idea
 → published on → Product Exchange

Idea
 → references → Product
 → creates → Supplier Search Request
 → has → Milestone
```

### Supplier & Sourcing
```
Supplier
 → has → Supplier Card
 → participates in → Order

Supplier Card
 → references → Product

Supplier Search Request
 → assigned to → Buyer          (Client сам или через Buyer)
```

### Orders
```
Order
 → created by → Client
 → processed by → Buyer
 → contains → Order Item        (Order Item → references → Product)
 → creates → Box
 → references → Supplier
 → references → Payment
 → has → Order Type
```

### Warehouse & Tasks
```
Warehouse
 → stores → Box
 → processes → Warehouse Task
 → prepares → Batch
 → managed by → Storekeeper

Warehouse Task
 → assigned to → Storekeeper
 → processes → Box

Box
 → contains → Product
 → belongs to → Order
 → belongs to → Batch
 → belongs to → Super Box
 → processed by → Warehouse Task
 → references → Destination
 → references → Tariff
 → stored in → Warehouse
 → goes through → Shipment       [NV]

Super Box
 → groups → Box
```

### Batches & Logistics
```
Batch
 → groups → Box
 → sent as → Shipment            [NV]
```

### Freelance / Services
```
Service Request
 → created by → Client
 → receives → Proposal
 → references → Service
 → has → Milestone

Proposal   → created by → Freelancer
Service    → created by → Freelancer
Announcement
 → references → Service
 → created by → Freelancer
```

### Access Control & Organization
```
User
 → has → Account
 → has → Role
 → has → Sub-user

Account
 → owns → Store / Product / Order

Sub-user
 → assigned to → Permission Preset
 → references → Product / Store

Permission Preset → contains → Permission
Role → has → Permission
```

### Marketplace & Stores
```
Marketplace → has → Store
Store
 → references → Marketplace
 → generates → Parsing Report
Niche → published on → Product Exchange
```

### Inventory
```
Inventory → contains → Product
Return
 → references → Product
 → references → Order            [NV]
Listing → generated from → Product
```

### Finance
```
Payment
 → references → Supplier
 → references → User
```

### Analytics & Advertising
```
Report
 → generated from → Product / Inventory
AI Tool → uses → Inventory
Campaign → references → Product
Voice of Customer
 → references → Product
 → references → Return
Dashboard → uses → Report        [NV]
```

### Collaboration, Support & Notifications
```
Notification → references → Order / Box / Tariff
Message → exchanged between → User
Support Ticket → created by → User
Feedback
 → answers → Support Ticket
 → created by → Admin/Moderator
```

### Administration & Integrations
```
Tariff → configured by → Storekeeper
Destination → configured by → Storekeeper
Parser → has → Parsing Profile / Parsing Request
Dynamic Column → extends → Product
Integration → connected to → Store
Tour → assigned to → Role
Milestone → attached to → Service Request / Idea
```

---

## 4. Relationship Statistics

- **Карточек сущностей** ([DOMAIN_MODEL](DOMAIN_MODEL.md) §4): **66**. Часть
  переклассифицирована из «сущностей» по ответам DM: `Inventory Item` = Product
  (DM2), `SKU/UPC/EAN` — атрибуты (DM13), `Listing` — набор отчётов (DM5),
  `Research Product` — статус Product (DM4), `Voice of Customer` — аналитический
  срез (DM12), `Connected App` — в разработке (DM6).
- **Total relationships:** **105**
- **Confirmed relationships:** **101**
- **Needs validation:** **4** (#44 Box→Shipment, #47 Batch→Shipment,
  #79 Return→Order, #87 Dashboard→Report)
- **Unknown cardinalities (`?`):** **50**

Top-10 сущностей по числу связей (source + target):

| # | Сущность | Связей (≈) |
|---|---|---|
| 1 | Product | 28 |
| 2 | Box | 16 |
| 3 | Order | 12 |
| 4 | Service Request | 7 |
| 5 | Store | 6 |
| 6 | User | 6 |
| 7 | Product Card | 5 |
| 8 | Idea | 5 |
| 9 | Warehouse | 5 |
| 10 | Supplier / Account / Inventory / Milestone | 4 |

---

## Validation Rules

- Точность важнее полноты. Не выдумываем сущности, глаголы, кардинальности,
  владение, lifecycle.
- Недостаточно данных → `Relationship = ?`, `Cardinality = ?`,
  `Status = Needs validation`, `Notes = ?`.
- Связи не дублируются; обратные связи помечены («обратная к #N»).
- Каждая `Needs validation` содержит `?` вместо предположений.
- Открытые вопросы по сущностям — в [DOMAIN_MODEL](DOMAIN_MODEL.md) §11 и трекере
  [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md).

> Единый источник правды по бизнес-связям. Основа для Knowledge Graph,
> таксономии Framer CMS, AI-ассистента, Academy, User Guide и будущей
> API-документации.
