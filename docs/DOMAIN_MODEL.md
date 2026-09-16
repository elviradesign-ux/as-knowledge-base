# Domain Model — Seller Exchange

> Семантическое ядро документации Seller Exchange (внутр. кодовое имя —
> **AmazonService / AS**). Описывает бизнес-концепции платформы: сущности,
> домены, роли, жизненные циклы — и связывает их с остальной базой знаний.
> **Связи между сущностями** вынесены в парный документ —
> [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md) (держим синхронно).
>
> Собран из существующей КБ: [MANIFESTO](MANIFESTO.md),
> [INFORMATION_ARCHITECTURE](INFORMATION_ARCHITECTURE.md), [GLOSSARY](GLOSSARY.md),
> [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md), [SCREEN_CATALOG](SCREEN_CATALOG.md),
> [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md), [ENTITY_STATES](ENTITY_STATES.md),
> [LOCALIZATION_GUIDE](LOCALIZATION_GUIDE.md),
> [articles/screens/inventory-products.md](articles/screens/inventory-products.md).
>
> **Принцип:** точность важнее полноты. Здесь только то, что подтверждено
> документацией. Непроверенное помечено **Needs validation** и вынесено в
> §11 Open Questions. Терминологические расхождения UI↔бэкенд приведены как есть.

---

## 1. Purpose

DOMAIN_MODEL.md — единый смысловой слой, на который опираются Marketplace
Academy, User Guide, Knowledge Base, таксономия Framer CMS, AI-ассистент,
поиск, онбординг и будущая API-документация. Он отвечает на вопрос «из каких
понятий состоит платформа и как они связаны», не привязываясь к реализации.

## 2. Scope

**Покрывает:** бизнес-сущности платформы, их связи, доменные области, роли,
модули, жизненные циклы, привязку к статьям КБ, известные интеграции.

**Сознательно НЕ является:**
- схемой базы данных;
- API-референсом (API `data_filters` и т.п. — в raw-доках, см.
  [CONTRIBUTING](CONTRIBUTING.md));
- ER-диаграммой;
- руководством по реализации.

Имена таблиц/полей бэкенда используются только как доказательства
существования сущности, а не как определение её структуры.

---

## 3. Core Domain Areas

Домены и их подтверждённые сущности (сущности, не подтверждённые КБ, помечены
**NV** = Needs validation):

| Домен | Сущности |
|---|---|
| Marketplace | Marketplace, Store/Shop, Niche |
| Organization | Account, User, Sub-user, Profile |
| Access Control | Role, Permission, Permission Preset |
| Product | Product (= Inventory Item), Product Card, Parent Product, Variation, ASIN, FNSKU, Barcode, Brand, Category, Tag, Transparency Code · _атрибуты:_ SKU, UPC, EAN |
| Product Research | Product Idea, Research Product _(=статус Product)_, Milestone |
| Supplier & Sourcing | Supplier, Supplier Card, Supplier Search Request, Strategy |
| Freelance / Services | Service, Service Request, Proposal, Announcement, Service Provider (role) |
| Orders | Order, Order Status, Order Type, Order Item, Payment |
| Inventory | Inventory, Listing _(=набор отчётов)_, Return |
| Warehouse | Warehouse, Box, Super Box, Batch, Warehouse Task, Destination, Tariff |
| Logistics | Shipment |
| Analytics | Report, Business Report, Dashboard, PPC Metrics, Voice of Customer _(=срез)_, Widget (NV) |
| Advertising | Campaign, PPC Metrics |
| Finance | Finance / Balance, Payment, Transaction |
| Collaboration | Message |
| Support | Support Ticket, Feedback |
| Notifications | Notification |
| Administration | Patch Note, Dynamic Field/Column, Dynamic Translation, Tour/Onboarding, Milestone, Parser (Parsing Profile / Parsing Request) |
| Integrations | Integration (Amazon SP, SellerBoard) |
| AI Tools | AI Tool (AI Analyzer / AI Assistant) |
| Apps Marketplace | _в разработке (DM6)_ |

---

## 4. Entity Catalog

Формат для каждой сущности: Definition · Business meaning · Modules · Roles ·
Related entities · Workflows · Screens · Glossary · Articles · Notes.
Прочерк «—» = в КБ не зафиксировано (не выдумываем).

### Marketplace
- **Definition:** региональный маркетплейс Amazon, на котором продаётся товар.
- **Business meaning:** определяет площадку продажи (Amazon.com — США и т.д.).
- **Modules:** Inventory, Stores, Reports. **Roles:** Client, Admin.
- **Related entities:** Store/Shop, Product, Listing. **Workflows:** WF-034.
- **Screens:** SCR-120, SCR-280. **Glossary:** поле «Маркетплейс» (Inventory).
- **Articles:** [inventory-products](articles/screens/inventory-products.md).
- **Notes:** бэкенд-поле `marketPlaceCountry` (алиасы `marketplace`,
  `marketPlaceCountryShortTitle`).

### Store / Shop
- **Definition:** подключённый аккаунт Amazon Seller Central.
- **Business meaning:** источник авто-обновляемых данных о товарах и продажах.
- **Modules:** Stores. **Roles:** Client.
- **Related entities:** Account, Marketplace, Product, Parsing Report.
- **Workflows:** WF-034. **Screens:** SCR-280, SCR-281, SCR-M47 (`ShopModal`).
- **Glossary:** Магазин (Store / Shop). **Articles:** —.
- **Notes:** бэкенд `shops` (`ownerId`, `is_active`); саб-юзеры ограничены
  `shopIds`.

### Niche
- **Definition:** нишевый раздел биржи товаров.
- **Business meaning:** витрина нишевых предложений на бирже.
- **Modules:** Product Exchange. **Roles:** Client.
- **Related entities:** Product, Product Card. **Workflows:** WF-005 (косвенно).
- **Screens:** SCR-162 (`NicheView`). **Glossary:** Ниша. **Articles:** —.

### Account
- **Definition:** учётная запись пользователя.
- **Business meaning:** идентичность пользователя на платформе; владеет
  магазинами, товарами, заказами; корень для саб-пользователей.
- **Modules:** Organization, Users. **Roles:** любые (учётка у пользователя
  любой роли). **Related entities:** User, Sub-user, Store.
- **Workflows:** —. **Screens:** SCR-016, SCR-017. **Glossary:** —.
- **Notes:** подтверждено (2026-07-01): Account = учётная запись пользователя;
  **Client** — только роль (основной пользователь платформы, CODE=10);
  **User = platform-user** — любой пользователь любой роли. Разграничение
  закрыто (DM3).

### User
- **Definition:** любой пользователь платформы любой роли (platform-user).
- **Business meaning:** субъект действий и прав; имеет учётную запись (Account)
  и роль.
- **Modules:** Users. **Roles:** все. **Related entities:** Account, Role,
  Sub-user, Profile.
- **Screens:** SCR-016, SCR-017, SCR-300 (`PlatformUsersView`), SCR-301.
- **Glossary:** Роль (косвенно). **Notes:** бэкенд `users` / `platform-users`.

### Sub-user
- **Definition:** участник команды пользователя (саб-юзер); может быть у роли
  любого типа.
- **Business meaning:** делегирование доступа к части продуктов/магазинов внутри
  команды пользователя.
- **Modules:** Users, Access Control. **Roles:** любые (у пользователя любой роли).
- **Related entities:** User, Permission, Permission Preset, Product, Store.
- **Workflows:** WF-060. **Screens:** SCR-301, SCR-M06 (`LinkSubUserModal`).
- **Glossary:** Саб-пользователь. **Notes:** доступ ограничен `applyAccessFilters`
  (см. data scoping в [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md)). Подтверждено
  (DM3): саб-юзер возможен у любой роли.

### Profile
- **Definition:** профиль пользователя.
- **Business meaning:** личные данные, достижения.
- **Modules:** Profile. **Roles:** все. **Related entities:** User, Achievement (NV).
- **Screens:** SCR-010 (`ProfileView`). **Glossary:** —.
- **Notes:** ачивки/геймификация упоминаются в wiki, в КБ-глоссарии не описаны →
  **Needs validation**.

### Role
- **Definition:** набор прав RBAC.
- **Business meaning:** определяет доступ к меню, данным и действиям.
- **Modules:** Access Control. **Roles:** все (Admin управляет).
- **Related entities:** Permission, Permission Preset, User.
- **Screens:** SCR-302. **Glossary:** Роль.
- **Notes:** 8 продуктовых ролей + служебные; коды в
  [ENTITY_STATES](ENTITY_STATES.md) (0=ADMIN…60=MODERATOR).
  ⚠️ Freelancer (UI) = Service Provider (роуты); Storekeeper = «warehouse»
  в таблицах бэкенда.

### Permission
- **Definition:** отдельное право доступа.
- **Business meaning:** атомарный доступ к фиче/данным внутри роли.
- **Modules:** Access Control. **Roles:** Admin, Buyer.
- **Related entities:** Role, Permission Preset, Sub-user.
- **Workflows:** WF-060. **Screens:** SCR-302, SCR-M06 (`PermissionsModal`,
  `SinglePermissionModal`, `GroupPermissionModal`). **Glossary:** —.

### Permission Preset
- **Definition:** именованный набор доступов, уточняющий права внутри роли.
- **Business meaning:** переиспользуемый шаблон прав.
- **Modules:** Access Control. **Roles:** Admin.
- **Related entities:** Permission, Role, Sub-user. **Workflows:** WF-060.
- **Screens:** SCR-302. **Glossary:** Пресет разрешений.
- **Notes:** подтверждено (DM10): **жизненного цикла нет** — это просто
  именованный набор прав.

### Product
- **Definition:** товар в каталоге, привязанный к ASIN.
- **Business meaning:** центральная сущность: продаётся, заказывается, хранится.
- **Modules:** Inventory, Product Exchange, Orders, Warehouse, Product Launch.
- **Roles:** Client, Admin, Buyer, Researcher, Supervisor.
- **Related entities:** Product Card, ASIN, Brand, Category, Tag, Supplier, Order, Box,
  Inventory, Idea. **Workflows:** WF-001…008, WF-030.
- **Screens:** SCR-120, SCR-121, SCR-123, SCR-124. **Glossary:** Карточка
  продукта. **Articles:** [inventory-products](articles/screens/inventory-products.md).
- **Notes:** бэкенд `products` — 197 фильтруемых колонок (≈ поля Инвентаря,
  см. GLOSSARY «Inventory — поля таблицы»).

### Product Card
- **Definition:** единица товара с данными ASIN, вариантами и статусом готовности.
- **Business meaning:** объект ресёрча/проверки/публикации на бирже.
- **Modules:** Product Research, Product Exchange, Inventory.
- **Roles:** Researcher, Supervisor, Buyer, Client.
- **Related entities:** Product, ASIN, Variation, Supplier Card, Idea.
- **Workflows:** WF-001, WF-002, WF-004. **Screens:** SCR-124, SCR-180, SCR-181.
- **Glossary:** Карточка продукта. **Notes:** статусы товара/карточки —
  [ENTITY_STATES](ENTITY_STATES.md) «Статусы товара» (0..300, ветка FROM_CLIENT_*).

### Parent Product / Variation
- **Definition:** товар может быть самостоятельным продуктом или вариацией
  другого; Parent указывает на связь и зависимость между продуктами.
- **Business meaning:** группировка связанных ASIN и зависимости между товарами.
- **Modules:** Product, Inventory. **Roles:** Client, Researcher.
- **Related entities:** Product, ASIN. **Workflows:** —. **Screens:** SCR-124.
- **Glossary:** поле «Вариация» (Inventory).
- **Notes:** подтверждено (DM18): Variation — это Product; Parent Product
  указывает на связь/зависимость. `addVariation`, `addParent`, `BindProductModal`.

### ASIN
- **Definition:** Amazon Standard Identification Number — идентификатор товара.
- **Business meaning:** ключ товара на Amazon; проверяется ASIN-чекером.
- **Modules:** Product, Inventory, Supervisor Settings. **Roles:** все продуктовые.
- **Related entities:** Product, Product Card, FNSKU. **Screens:** SCR-320.
- **Glossary:** ASIN. **Notes:** массовые операции — `addListOfAsin`,
  `deleteSelectedAsins`.

### SKU — атрибут (не сущность)
- **Definition:** складская единица (артикул) продавца.
- **Business meaning:** идентификация позиции продавца.
- **Notes:** подтверждено (DM13): **SKU / UPC / EAN — атрибуты**, а не отдельные
  сущности (SKU — атрибут Product, UPC/EAN — атрибуты Barcode).
- **Related entities:** Product (атрибут). **Glossary:** —.

### FNSKU
- **Definition:** Fulfillment Network SKU — внутренний код Amazon для FBA.
- **Business meaning:** отслеживание товара на складах FBA.
- **Modules:** Inventory, Warehouse. **Related entities:** Product, Barcode, Box.
- **Glossary:** Fnsku (Inventory). **Notes:** —.

### Barcode (UPC / EAN)
- **Definition:** штрихкод товара (UPC, EAN или внутренний FNSKU).
- **Business meaning:** идентификация и приёмка на складе.
- **Modules:** Inventory, Warehouse. **Roles:** Client, Storekeeper.
- **Related entities:** Product, FNSKU, Box. **Screens:** SCR-120, SCR-202.
- **Glossary:** Баркод (Inventory). **Notes:** `addBarcode`, `BarHsCodeModal`,
  `addProductBarcodeToBox`. Подтверждено (DM13): **UPC/EAN — атрибуты** Barcode,
  не отдельные сущности.

### Brand
- **Definition:** бренд/торговая марка товара.
- **Modules:** Product, Inventory. **Related entities:** Product, Category.
- **Glossary:** поле Brand (Inventory).
- **Notes:** DM17: **Brand Launch** — отдельный процесс, связанный с Product
  Launch (несколько успешных Product Launch = Brand Launch): стратегия продавца
  от запуска продукта до собственного бренд-маркетплейса. Отдельного раздела/
  флоу пока нет, описание стратегии отсутствует → детали **Needs validation**.

### Category
- **Definition:** категория/подкатегория товара на Amazon.
- **Modules:** Product, Inventory, Admin Settings. **Related entities:** Product.
- **Glossary:** поля Category/Subcategory (Inventory). **Screens:** SCR-M
  (`CategoryModal`, Admin → Настройки). **Notes:** —.

### Tag
- **Definition:** ключевое слово для внутреннего поиска/сегментации товаров.
- **Modules:** Product, Inventory, Admin Settings. **Roles:** Client, Admin.
- **Related entities:** Product. **Screens:** SCR-120 (actions), Admin Settings/Tags.
- **Glossary:** поле «Теги» (Inventory). **Notes:** `addTag`,`deleteSelectedTags`,
  `TagsModal`, `TagsListModal`, бэкенд `tags`.

### Transparency Code
- **Definition:** признак участия товара в программе Amazon Transparency.
- **Business meaning:** защита от подделок.
- **Modules:** Inventory. **Related entities:** Product. **Glossary:** поле Transparency
  Codes (Inventory). **Notes:** —.

### Product Idea (Idea)
- **Definition:** кандидат на запуск товара, проходящий пайплайн.
- **Business meaning:** воронка выбора и запуска нового товара.
- **Modules:** Product Launch. **Roles:** Client, Buyer.
- **Related entities:** Product, Product Card, Supplier Search Request.
- **Workflows:** WF-032. **Screens:** SCR-140…SCR-146, SCR-M07 (`IdeaModal`).
- **Glossary:** Идея / Запуск товара. **Notes:** статусы идеи —
  [ENTITY_STATES](ENTITY_STATES.md) «Статусы идеи» (в источнике подпись
  «Box Status», подтверждено что это идея). Бэкенд `ideas` (8 колонок).

### Research Product — статус Product (не сущность)
- **Definition:** товар в диапазоне статусов ресёрча (0–15 / 200–205).
- **Business meaning:** товар на стадии исследования, видим Researcher и Buyer.
- **Modules:** Product Research. **Roles:** Researcher, Buyer.
- **Related entities:** Product, Product Card, Idea. **Workflows:** WF-001, WF-003.
- **Screens:** SCR-123. **Glossary:** —.
- **Notes:** подтверждено (DM4): **не отдельная сущность**, а Product в статусах
  0–15 / 200–205. Возможна связь с Idea — уточняется (частично **Needs validation**).

### Milestone
- **Definition:** веха (этап) — глобальная настраиваемая точка процесса.
- **Business meaning:** контроль прохождения этапов заявки/идеи.
- **Modules:** Administration, Freelance/Services, Product Launch.
  **Roles:** Admin (настройка), Client, Freelancer.
- **Related entities:** Service Request, Idea. **Screens:** SCR-M
  (`MilestonesModal`, `MilestonesDetailsModal`), Admin → Настройки → Вехи.
- **Glossary:** —. **Notes:** подтверждено (DM11): глобальная сущность,
  крепится к **Service Request** (раздел Service Provider) и к **Idea**
  (раздел Product Launch). Бэкенд `milestones` (`createdById`).

### Supplier
- **Definition:** поставщик товара.
- **Business meaning:** источник закупки; находится Buyer, верифицируется Supervisor.
- **Modules:** Supplier & Sourcing, Orders. **Roles:** Buyer, Supervisor.
- **Related entities:** Supplier Card, Product, Order. **Workflows:** WF-003, WF-020.
- **Screens:** SCR-190, SCR-M (`SupplierModal`,`AddSupplierModal`).
- **Glossary:** Поставщик. **Notes:** бэкенд `supplier` (`createdById`),
  биржа поставщиков — `status=PUBLISHED`.

### Supplier Card
- **Definition:** карточка поставщика (набор данных о предложении поставщика).
- **Business meaning:** привязывается к товару/идее, публикуется на бирже.
- **Modules:** Supplier & Sourcing, Product Exchange. **Roles:** Buyer, Supervisor,
  Client. **Related entities:** Supplier, Product, Order, Idea.
- **Screens:** SCR-161, SCR-M (`SupplierCardModal`,`BindSupplierCardModal`,
  `WholesaleCardModal`). **Glossary:** —.
- **Notes:** статусы — [ENTITY_STATES](ENTITY_STATES.md) «Статус карточки
  поставщика» (IS_BEING_COLLECTED / HAS_DISPATCHED). Бэкенд `supplierCard`.

### Supplier Search Request
- **Definition:** запрос на поиск поставщика.
- **Business meaning:** поиск поставщика под товар/идею; доступен нескольким
  ролям — Client может искать поставщиков **самостоятельно** или **через Buyer**.
- **Modules:** Supplier & Sourcing, Product Launch. **Roles:** Client, Buyer,
  Supervisor. **Related entities:** Supplier, Product Card, Idea. **Workflows:** WF-003.
- **Screens:** SCR-191, SCR-192 (`SearchSupplierView`). **Glossary:** —.
- **Notes:** подтверждено (DM7): выделен отдельно, т.к. процесс мульти-ролевой
  (Client напрямую или через Buyer). Отражается ветвями статусов товара
  (TO_BUYER_FOR_RESEARCH, FROM_CLIENT_*).

### Strategy
- **Definition:** стратегия сорсинга (DROPSHIPPING, PRIVATE_LABEL,
  ONLINE_ARBITRAGE_CHINA, WHOLESALE_USA).
- **Business meaning:** способ закупки/бизнес-модель товара.
- **Modules:** Product, Product Research. **Roles:** Client, Buyer.
- **Related entities:** Product, Idea. **Glossary:** поле «Стратегия» (Inventory).
- **Notes:** [ENTITY_STATES](ENTITY_STATES.md) «Стратегия сорсинга» (в источнике
  подпись «Task Priority», подтверждено что это стратегия). Wholesale — вес 40.

### Service
- **Definition:** услуга фрилансера (Service Provider) на бирже услуг.
- **Business meaning:** предложение фриланс-услуг для запусков на Amazon.
- **Modules:** Freelance / Services. **Roles:** Freelancer (Service Provider).
- **Related entities:** Service Request, Proposal. **Workflows:** WF-051.
- **Screens:** SCR-265, SCR-M (`ServiceModal`,`CreateServiceModal`).
- **Glossary:** —. **Notes:** вариации услуги — `CreateServiceVariationModal`.

### Service Request (Request)
- **Definition:** заявка клиента на услугу на бирже.
- **Business meaning:** спрос на фриланс-услугу; на неё откликаются Proposal'ами.
- **Modules:** Freelance / Services. **Roles:** Client, Freelancer.
- **Related entities:** Service, Proposal. **Workflows:** WF-033, WF-050.
- **Screens:** SCR-260, SCR-261, SCR-262, SCR-M (`CreateRequestModal`,
  `RequestModal`). **Glossary:** —.
- **Notes:** бэкенд `requests` (`type='CUSTOM'`), `kind=MY/VACANT`.

### Proposal
- **Definition:** предложение фрилансера в ответ на заявку.
- **Business meaning:** отклик исполнителя на Service Request.
- **Modules:** Freelance / Services. **Roles:** Freelancer, Client.
- **Related entities:** Service Request, Service. **Workflows:** WF-050.
- **Screens:** SCR-263, SCR-264, SCR-M (`ProposalModal`). **Glossary:** —.
- **Notes:** бэкенд `proposals` (`createdById`). Actions `acceptDeal`/`rejectProposal`.

### Order
- **Definition:** запрос клиента на закупку товара.
- **Business meaning:** ядро операционного потока; обрабатывается Buyer,
  комплектуется Storekeeper.
- **Modules:** Orders. **Roles:** Client, Buyer, Admin.
- **Related entities:** Product, Supplier, Box, Batch, Payment, Order Item (NV).
- **Workflows:** WF-005, WF-006, WF-022, WF-023, WF-024, WF-030, WF-031.
- **Screens:** SCR-100…107, SCR-M01 (`CreateOrderModal`), SCR-M03 (`EditOrderModal`).
- **Glossary:** Заказ, Статус заказа. **Articles:**
  [inventory-products](articles/screens/inventory-products.md) (создание).
- **Notes:** статусы — [ENTITY_STATES](ENTITY_STATES.md) (0 FORMED…50 SHIPPED);
  типы — Order Type. Бэкенд `orders` (22 колонки).

### Order Status
- **Definition:** этап жизненного цикла заказа.
- **Related entities:** Order. **Glossary:** Статус заказа.
- **Notes:** канонические коды в [ENTITY_STATES](ENTITY_STATES.md); текстовая
  цепочка вида Buyer — в [GLOSSARY](GLOSSARY.md).

### Order Type
- **Definition:** тип заказа (LONG / STANDARD / URGENT / PROBLEMATIC).
- **Related entities:** Order. **Notes:** [ENTITY_STATES](ENTITY_STATES.md) «Типы заказа».

### Order Item
- **Definition:** связка сущностей, принадлежащая Заказу (позиция заказа).
- **Business meaning:** объединяет товар и связанные с ним объекты в рамках
  одного заказа.
- **Modules:** Orders. **Roles:** Client, Buyer.
- **Related entities:** Order, Product. **Workflows:** WF-030, WF-031.
- **Screens:** SCR-M01 (`CreateOrderModal`). **Glossary:** —.
- **Notes:** подтверждено (DM1): Order Item — связка сущностей, принадлежащая
  Заказу (Order содержит Order Item'ы).

### Payment
- **Definition:** платёж (в т.ч. оплата поставщику).
- **Business meaning:** денежное движение по заказу/поставщику.
- **Modules:** Orders, Finance. **Roles:** Buyer, Client, Admin.
- **Related entities:** Order, Supplier, Finance/Balance. **Workflows:** WF-023.
- **Screens:** SCR-M (`SupplierPaymentModal`,`PaymentMethodsModal`).
- **Glossary:** —. **Notes:** бэкенд `payments` (`recipient_id`).

### Inventory
- **Definition:** каталог товаров клиента с аналитикой запасов/продаж/финансов.
- **Business meaning:** операционный обзор товаров и точка создания заказов.
- **Modules:** Inventory. **Roles:** Client, Admin.
- **Related entities:** Product, Listing, Order, Box, Report. **Workflows:** WF-030.
- **Screens:** SCR-120, SCR-121, SCR-122. **Glossary:** раздел «Inventory —
  поля таблицы» (~180 полей). **Articles:**
  [inventory-products](articles/screens/inventory-products.md).

### Inventory Item = Product (карточка товара пользователя)
- **Definition:** карточка товара пользователя в его Инвентаре, за которой он
  закрепляет ASIN и к которой привязывает купленную на бирже Supplier Card.
- **Business meaning:** «свой» товар пользователя (в отличие от Supplier Card —
  предложения поставщика, которое покупается на бирже и привязывается сюда).
- **Modules:** Inventory. **Roles:** Client, Admin.
- **Related entities:** Product, ASIN, Supplier Card.
- **Glossary:** Карточка продукта. **Notes:** подтверждено (DM2):
  **Inventory Item = Product**. Статусы VACANT/RESERVED/WAITING_INVITE/INVITED/
  REGISTERED/READY_TO_CHECKING/IN_USE/UNLINKED
  ([ENTITY_STATES](ENTITY_STATES.md)) — это статусы карточки товара
  пользователя **в связке с Supplier Card**.

### Listing — набор отчётов (не сущность)
- **Definition:** набор отчётов по листингу товара на Amazon.
- **Business meaning:** состояние листинга через отчёты.
- **Modules:** Inventory. **Roles:** Client. **Related entities:** Product, Report.
- **Screens:** SCR-122 (Inventory reports). **Glossary:** —.
- **Notes:** подтверждено (DM5): **Listing — это набор отчётов**, а не отдельная
  сущность. Бэкенд `productListingReports`.

### Return
- **Definition:** возврат товара.
- **Modules:** Inventory, Logistics. **Roles:** Client.
- **Related entities:** Product, Order. **Screens:** SCR-M (`ReturnDetailsModal`).
- **Glossary:** поле Returns (Inventory). **Notes:** бэкенд `inventoryReturns`.

### Warehouse
- **Definition:** склад (преп-центр) хранения и обработки товара.
- **Business meaning:** приёмка, хранение, распределение, формирование партий.
- **Modules:** Warehouse, Warehouse Management. **Roles:** Storekeeper, Client, Admin.
- **Related entities:** Box, Batch, Task, Tariff, Destination, Shipment.
- **Workflows:** WF-007, WF-042. **Screens:** SCR-200…205, SCR-203.
- **Glossary:** Склад (косвенно). **Notes:** локации: AS China, AS USA, AWD,
  преп-центры (см. Inventory-поля и Shipment status).

### Box
- **Definition:** физическая единица хранения/отправки товара.
- **Business meaning:** атом складского учёта; группируется/делится/мёржится.
- **Modules:** Warehouse, Orders, Batches. **Roles:** Client, Storekeeper, Admin.
- **Related entities:** Product, Order, Batch, Task, Destination, Tariff.
- **Workflows:** WF-007, WF-031, WF-035. **Screens:** SCR-200, SCR-202, SCR-204,
  SCR-M04 (`CreateBoxModal`), SCR-M05 (`GroupingBoxesModal`), `BoxModal`,
  `EditBoxModal`, `MergeBoxesModal`, `RedistributeBoxModal`.
- **Glossary:** Коробка. **Notes:** бэкенд `boxes` (33 колонки, `status`,`xid`,
  `destination`,`logicsTariff`,`storekeeper`,`client`).

### Super Box (SB)
- **Definition:** контейнер из коробок (обозначается **SB**).
- **Business meaning:** объединяет несколько Box в один контейнер.
- **Modules:** Warehouse. **Roles:** Storekeeper, Client.
- **Related entities:** Box. **Screens:** SCR-M05 (`GroupingBoxesModal`),
  `MergeBoxesModal`. **Glossary:** —.
- **Notes:** подтверждено (DM14): Super Box существует, контейнер из коробок, SB.

### Batch
- **Definition:** группа коробок, отправляемых вместе.
- **Business meaning:** единица отгрузки на Amazon; имеет Prep ID.
- **Modules:** Batches, Warehouse. **Roles:** Client, Storekeeper, Admin.
- **Related entities:** Box, Shipment, Product, Order. **Workflows:** WF-035, WF-041.
- **Screens:** SCR-240…242, SCR-M (`BatchInfoModal`,`EditBatchModal`,
  `RequestToSendBatchModal`,`GeneratePrepIdModal`). **Glossary:** Партия.
- **Notes:** бэкенд `batches` (28 колонок), статусы: awaiting-send/sent/archive.

### Warehouse Task (Task)
- **Definition:** складская задача (приёмка/редактирование/разделение/объединение).
- **Business meaning:** единица работы Storekeeper над коробками.
- **Modules:** Tasks. **Roles:** Storekeeper, Client, Admin.
- **Related entities:** Box, Product, Order. **Workflows:** WF-040.
- **Screens:** SCR-220…223, SCR-M (`EditTaskModal`,`ReceiveBoxModal`).
- **Glossary:** —. **Notes:** типы — [ENTITY_STATES](ENTITY_STATES.md) «Типы
  задач» (receive/edit/storekeeperEditBoxes/split/merge); бэкенд `tasks` (9 кол.).

### Destination
- **Definition:** пункт назначения (адрес/место выгрузки).
- **Business meaning:** куда отправляется коробка/партия.
- **Modules:** Warehouse Management, Admin Settings. **Roles:** Storekeeper, Admin.
- **Related entities:** Box, Batch, Tariff. **Screens:** SCR-M (`DestinationModal`),
  Admin → Настройки → Пункты назначения. **Glossary:** —.

### Tariff
- **Definition:** стоимость логистики/хранения по региону.
- **Business meaning:** ценообразование складских/логистических операций.
- **Modules:** Warehouse Management. **Roles:** Storekeeper.
- **Related entities:** Box, Order, Destination. **Workflows:** WF-042.
- **Screens:** SCR-203, SCR-M (`TariffModal`,`LogisticsTariffModal`).
- **Glossary:** Тариф. **Notes:** бэкенд `tariff_type=20` (логистический).

### Shipment
- **Definition:** движение товара/коробок между складами (Китай → партия → США).
- **Business meaning:** логистический жизненный цикл товара.
- **Modules:** Logistics, Warehouse. **Roles:** Storekeeper, Client.
- **Related entities:** Box, Batch, Warehouse. **Screens:** SCR-240, SCR-241.
- **Glossary:** —. **Notes:** статусы — [ENTITY_STATES](ENTITY_STATES.md)
  «Статусы товара на складе/отгрузки»; бэкенд `inventoryShipments`.

### Report / Business Report
- **Definition:** отчёт (по продажам, инвентарю, аккаунту, PPC и т.д.).
- **Business meaning:** аналитический срез данных.
- **Modules:** Analytics, Inventory. **Roles:** Client, Manager/Supervisor, Admin.
- **Related entities:** Product, Inventory, Campaign, Store. **Screens:** SCR-122,
  SCR-281, SCR-M (`ReportModal`). **Glossary:** —.
- **Notes:** множество типов отчётов (ORDERS, INVENTORY, RETURNS, BUSINESS_REPORTS,
  INCOME, TRANSACTIONS, VOICE, FBA_INVENTORY и др.) подтверждены raw-докой
  data_filters; их продуктовые определения в КБ пока не расписаны → §11.

### Dashboard
- **Definition:** сводный экран показателей роли.
- **Modules:** Dashboard. **Roles:** все (свой дэшборд на роль).
- **Related entities:** Report, Widget (NV). **Screens:** SCR-011. **Glossary:** —.
- **Notes:** Widget как сущность — **Needs validation**.

### PPC Metrics / Campaign
- **Definition:** рекламные кампании Amazon и их метрики.
- **Business meaning:** платное продвижение и его эффективность.
- **Modules:** Advertising, Analytics. **Roles:** Client.
- **Related entities:** Product, Report. **Glossary:** поля рекламы (Inventory:
  Adv Sales, Tacos, Acos, Adv Cpc, Adv Ctr…).
- **Notes:** отчёты CAMPAIGNS, PPC_ORGANIC, PPC_SALES_WEEKS/DAYS (raw data_filters).

### Voice of Customer — аналитический срез (не сущность)
- **Definition:** отчёт Voice парсинга: показатели возвратов — процент возвратов
  (`concession_rate`) и статус бейджа возвратов (`badge_status`).
- **Business meaning:** качество клиентского опыта по возвратам; расширяет модуль
  NCX rating критерием **Return Badge**.
- **Modules:** Analytics, Stores (парсинг). **Roles:** все (по местам размещения).
  **Related entities:** Product, Store, Return.
- **Glossary:** поля Pcx Health, Ncx Orders, Ncx Rate (Inventory).
- **Notes:** подтверждено (DM12): **аналитический срез, не отдельная сущность**.
  Данные `concession_rate`/`badge_status` сохраняются в БД интеграций, выводятся
  в отчёт «Магазины → Отчёты по парсингу → Voice» и в таблицу инвентаря;
  критерий Return Badge добавляется в модуль NCX rating (модалки продукта,
  заказа, коробки, задачи — Client/Buyer/Storekeeper). Star rating исключён.

### Review
- **Definition:** отзыв покупателя (оценка + текст).
- **Modules:** Analytics, Supplier & Sourcing. **Roles:** Client.
- **Related entities:** Product, Supplier. **Screens:** SCR-M (`ReviewsModal`,
  `LeaveFeedbackModal`). **Glossary:** поля Rating/Reviews (Inventory).

### Finance / Balance
- **Definition:** финансовый баланс и движение средств.
- **Business meaning:** учёт доходов/расходов, пополнение/вывод.
- **Modules:** Finance. **Roles:** почти все. **Related entities:** Payment, Transaction.
- **Workflows:** WF-071. **Screens:** SCR-012, SCR-M (`AdminBalanceModal`,
  `UserMoneyTransferModal`). **Glossary:** —.
- **Notes:** отчёты INCOME, TRANSACTIONS, TOTAL_BALANCE (raw data_filters).

### Notification
- **Definition:** уведомление пользователю.
- **Business meaning:** оповещение о событиях (заказы, коробки, тарифы, заявки).
- **Modules:** Notifications. **Roles:** Client, Buyer, Storekeeper, Freelancer, Admin.
- **Related entities:** Order, Box, Tariff, Service Request. **Screens:** SCR-013.
- **Glossary:** —. **Notes:** бэкенд `user_notifications`; у Client 5 вкладок.

### Message
- **Definition:** сообщение во внутреннем чате.
- **Modules:** Collaboration (Messages). **Roles:** все кроме Researcher.
- **Related entities:** User. **Workflows:** WF-073. **Screens:** SCR-014,
  SCR-M (`CreateNewChatModal`,`ForwardMessagesModal`). **Glossary:** —.

### Announcement — карточка услуги (объявление)
- **Definition:** объявление Service Provider (Freelancer) о предоставляемой
  услуге — карточка Услуги.
- **Business meaning:** витрина услуги фрилансера на бирже.
- **Modules:** Freelance / Services. **Roles:** Freelancer (создаёт), Client (видит).
- **Related entities:** Service, Freelancer.
- **Screens:** SCR-M (`SelectAnnouncementModal`). **Glossary:** —.
- **Notes:** подтверждено (DM16): объявление поставщика услуг об услуге
  (карточка Услуги). Бэкенд `announcements` (`createdById != userId` в vac).

### Support Ticket
- **Definition:** запрос пользователя в поддержку.
- **Business meaning:** обращение пользователя; проходит статусы обработки.
- **Modules:** Support. **Roles:** все (создают), Admin/Moderator (обрабатывают).
- **Related entities:** User, Feedback.
- **Workflows:** WF-072. **Screens:** SCR-015, SCR-M (`CreateTicketModal`,
  `TicketModal`). **Glossary:** —.
- **Notes:** подтверждено (DM9): Support Ticket = запрос пользователя. Статусы
  обработки — [ENTITY_STATES](ENTITY_STATES.md) «Статус обращения» (Новый →
  В обработке → Принято → Выполнено / Отклонено / Нужна информация).

### Feedback
- **Definition:** ответ Админа/модератора на запрос пользователя (Support Ticket).
- **Business meaning:** реакция поддержки на обращение (не путать с Review).
- **Modules:** Support. **Roles:** Admin, Moderator (создают ответ).
- **Related entities:** Support Ticket, User. **Glossary:** —.
- **Notes:** подтверждено (DM9): Feedback = ответ Админа/модератора на Support
  Ticket. Ранее статусы «обращения» ([ENTITY_STATES](ENTITY_STATES.md)) относятся
  к жизненному циклу Support Ticket. Бэкенд `feedback`.

### Patch Note
- **Definition:** запись об обновлении платформы.
- **Modules:** Administration. **Roles:** Admin, Moderator (просмотр — все).
- **Related entities:** —. **Screens:** SCR-018, SCR-M (`PatchNoteModal`). **Glossary:** —.

### Dynamic Field / Dynamic Column / Dynamic Translation
- **Definition:** настраиваемые поля, вычисляемые колонки, переводы строк.
- **Business meaning:** конфигурируемость таблиц и локализации без релиза.
- **Modules:** Administration. **Roles:** Admin. **Related entities:** Product, Report.
- **Screens:** SCR-306, SCR-307, SCR-M (`DynamicFieldModal`,`TranslationModal`).
- **Glossary:** —. **Notes:** привязка колонок — wiki «Column Binding»; бэкенд
  `dynamicColumns`, `DYNAMIC_COLUMNS: ["*"]` в data_filters.

### Tour / Onboarding
- **Definition:** обучающий тур/сценарий онбординга.
- **Modules:** Administration. **Roles:** Admin (настройка), все (прохождение).
- **Related entities:** Role. **Screens:** SCR-308, SCR-M (`ToursModal`). **Glossary:** —.
- **Notes:** бэкенд `tours` (видимость по роли: role=user.role OR -1).

### Parser (Parsing Profile / Parsing Request)
- **Definition:** механизм парсинга и его профили/запросы.
- **Business meaning:** сбор внешних данных (напр., по магазинам/ASIN).
- **Modules:** Administration (Admin), Stores (отчёты парсинга у Client).
- **Roles:** Admin; Client — отчёты. **Related entities:** Store, Product, Report.
- **Screens:** SCR-303, SCR-304, SCR-281, SCR-M (`ParsingProfileModal`,
  `ParsingReportsModal`,`ProfilesModal`). **Glossary:** —.

### Integration
- **Definition:** внешняя интеграция данных.
- **Business meaning:** источники данных: Amazon SP-API, SellerBoard.
- **Modules:** Integrations, Inventory, Analytics. **Roles:** Client, Admin.
- **Related entities:** Store, Report, Inventory. **Glossary:** —.
- **Notes:** подтверждено эндпоинтами `integrations/*` и полями SellerBoard
  (raw data_filters); в КБ отдельного описания интеграций нет → §11.

### AI Tool
- **Definition:** AI-анализ данных (AI Analyzer / AI Assistant).
- **Business meaning:** аналитика по фильтрам инвентаря, ассистент.
- **Modules:** AI Tools, Inventory. **Roles:** Client.
- **Related entities:** Inventory, Product. **Screens:** SCR-120, SCR-M (`AiAssistantModal`,
  `ToolsModal`,`ToolModal`). **Glossary:** —.
- **Notes:** AI Chat = модалка (из памяти проекта). Границы фичи — **Needs validation**.

### Connected App / Apps Marketplace — в разработке
- **Notes:** DM6 (2026-07-01): функционал **в разработке**. Пока моделируется
  только «Integration» (Amazon SP, SellerBoard). Вернуться, когда фича появится.

---

## 5. Relationships

Детальное описание связей между сущностями вынесено в отдельный документ —
**[ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md)** (единый источник правды по
бизнес-связям: таблица связей с кардинальностью и evidence, граф связей по
доменам, статистика). Здесь, в каталоге сущностей (§4), для каждой сущности
приведён только короткий список **Related entities** — без описания самих связей.

---

## 6. Role-to-Entity Matrix

Источник: [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md), [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md).

| Role | Main Entities | Typical Actions | Related Workflows |
|---|---|---|---|
| Client | Product, Inventory, Order, Box, Batch, Store, Idea, Service Request | Создать заказ, распределить по коробкам, запустить товар, отправить партию, запросить услугу | WF-005, WF-030, WF-031, WF-032, WF-033, WF-034, WF-035 |
| Buyer | Order, Supplier, Supplier Card, Product (research), Payment | Взять свободный заказ, найти поставщика, оплатить, ввести трек-номер | WF-003, WF-006, WF-022, WF-023, WF-024 |
| Storekeeper | Box, Batch, Warehouse Task, Tariff, Destination, Shipment | Принять коробки, выполнить задачу, сформировать партию, настроить тариф | WF-007, WF-040, WF-041, WF-042 |
| Supervisor | Product Card, Supplier, ASIN | Проверить карточку, верифицировать поставщика, настроить ASIN-чекер | WF-002, WF-004, WF-020, WF-021 |
| Researcher | Product Card, Product | Создать карточку товара | WF-001 |
| Admin | User, Permission Preset, все сущности (надзор), Parser, Dynamic* | Настроить права/онбординг, парсинг, конфигурация | WF-060, WF-061, WF-062, WF-063 |
| Service Provider (Freelancer) | Service, Service Request, Proposal | Опубликовать услугу, откликнуться предложением | WF-050, WF-051 |

## 7. Module-to-Entity Matrix

| Module | Primary Entities | Secondary Entities | Workflows | Articles |
|---|---|---|---|---|
| Inventory | Product, Inventory, Listing | Order, Box, Tag, Report | WF-030 | [inventory-products](articles/screens/inventory-products.md) |
| Orders | Order, Payment | Product, Box, Supplier | WF-005, WF-006, WF-030 | — |
| Product Launch | Idea | Product Card, Supplier Search Request | WF-032 | — |
| Product Exchange | Product Card, Supplier Card, Niche | Product | WF-005 | — |
| Ready to check | Product Card | ASIN, Supplier | WF-002, WF-004 | — |
| Suppliers | Supplier, Supplier Card | Product, Order | WF-003 | — |
| Warehouse | Box, Warehouse Task | Batch, Destination, Tariff, Shipment | WF-007, WF-040 | — |
| Batches | Batch | Box, Shipment | WF-035, WF-041 | — |
| Warehouse Management | Tariff, Destination | Warehouse | WF-042 | — |
| Freelance/Service Exchange | Service, Service Request, Proposal | User | WF-033, WF-050, WF-051 | — |
| Stores | Store | Marketplace, Parsing Report | WF-034 | — |
| Finance | Finance/Balance, Payment | Transaction | WF-071 | — |
| Users & Permissions | User, Sub-user, Role, Permission Preset | — | WF-060 | — |
| Messages | Message | User | WF-073 | — |
| Notifications | Notification | Order, Box, Tariff | — | — |
| Support | Support Ticket, Feedback | User | WF-072 | — |
| Parsing | Parser, Parsing Profile/Request | Store, Report | WF-063 | — |
| Settings (Admin) | Dynamic Field/Column/Translation, Tour, Category, Tag, Milestone, Destination | — | WF-061, WF-062 | — |
| AI Tools | AI Tool | Inventory, Product | — | — |
| Dashboard | Dashboard | Report | — | — |

---

## 8. Entity Lifecycle

Коды — из [ENTITY_STATES](ENTITY_STATES.md). Полные списки там; здесь — суть.

- **Product / Product Card:** NEW_PRODUCT(0) → RESEARCHER_CREATED(5) →
  RESEARCHER_FOUND_SUPPLIER(10) → CHECKED_BY_SUPERVISOR(15) →
  TO_BUYER_FOR_RESEARCH(30) → BUYER_PICKED(35) → BUYER_FOUND_SUPPLIER(40) →
  COMPLETE_SUCCESS(70) → PURCHASED(75). Отклонения: 20/25/50/60/80/90/100.
  Ветка «от клиента»: 200…300 (FROM_CLIENT_*).
- **Product Idea:** New(5) → On checking(10) → Supplier search(13) →
  Supplier found(14)/not found(15) → Card creating(16) → Adding ASIN(18) →
  Realized(20) / Rejected(25) / Closed(30).
- **Order:** FORMED(0)/NEW(1) → PENDING(2) → READY_FOR_BUYOUT(3) →
  READY_TO_PROCESS(10) → AT_PROCESS(15) → READY_FOR_PAYMENT(16) →
  PARTIALLY_PAYMENT(17) → [NEED_CONFIRMING_TO_PRICE_CHANGE(19)] →
  PAID_TO_SUPPLIER(20) → TRACK_NUMBER_ISSUED(25) → NEED_CONFIRMING_RECEIVING(27)
  → IN_STOCK(30) → AWAITING_SHIPMENT(45) → SHIPPED(50). Отмена: 35/40.
- **Supplier Request:** отражается статусами товара (TO_BUYER_FOR_RESEARCH →
  BUYER_FOUND_SUPPLIER / SUPPLIER_WAS_NOT_FOUND). Как самостоятельный
  жизненный цикл — **Needs validation**.
- **Box / Shipment (на складе):** NEW (в пути на преп Китая) →
  ACCEPTED_IN_PROCESSING → IN_STOCK → REQUESTED_SEND_TO_BATCH →
  [NEED_TO_UPDATE_THE_TARIFF / NEED_CONFIRMING_TO_DELIVERY_PRICE_CHANGE] →
  IN_BATCH → IN_BATCH_ON_THE_WAY → FINISH_PREP_CENTR_USA.
- **Batch:** awaiting-send → sent → archive (статусные вкладки; числовых кодов
  в КБ нет → **Needs validation** на точные состояния).
- **Support Ticket:** — в КБ нет статусов → **Needs validation**.
- **Feedback:** Новый(10) → В обработке(20) → Принято(30) → Выполнено(35) /
  Отклонено(40) / Нужна информация(50).
- **Permission Preset:** статусы в КБ отсутствуют → **Needs validation**.
- **Supplier Card:** IS_BEING_COLLECTED → HAS_DISPATCHED.
- **Business model (публикация):** DRAFT(0) → ON_HOLD(5) → PUBLISHED(10)
  (применяется к публикуемым сущностям, напр. поставщикам/картам на бирже).

---

## 9. Knowledge Base Mapping

Рекомендации по статьям для ключевых сущностей (статус — что уже есть / нужно):

| Entity | Glossary | User Guide | Workflow | FAQ | Academy |
|---|---|---|---|---|---|
| Product / Product Card | ✅ есть | нужна | WF-001/002 | нужна | «Как устроен товар» |
| Order | ✅ есть | нужна | WF-006 | «Почему заказ завис» | «Жизненный цикл заказа» |
| Inventory | ✅ (поля) | ✅ [inventory-products] | WF-030 | нужна | «Чтение таблицы инвентаря» |
| Box / Batch | нужна (Коробка✅, Партия✅) | нужна | WF-007/035/041 | нужна | «Склад и партии» |
| Idea / Product Launch | ✅ есть | нужна | WF-032 | нужна | «Запуск товара» |
| Supplier / Supplier Card | ✅ (Поставщик) | нужна | WF-003 | нужна | — |
| Service Request / Proposal | нужна | нужна | WF-033/050 | нужна | «Биржа услуг» |
| Permission Preset | нужна | нужна | WF-060 | нужна | — |
| Tariff / Destination | Тариф✅ | нужна | WF-042 | нужна | — |

## 10. Framer CMS Mapping (рекомендация)

Предлагаемые коллекции и поля (проект — не окончательная схема):

**Articles**
- `title`, `slug`, `section` (из [INFORMATION_ARCHITECTURE](INFORMATION_ARCHITECTURE.md)),
  `audience` (роли), `status` (draft/review/published), `locale` (en/ru/zh/ua),
  `owner`, `updated`, `body`, отношения: `relatedEntities[]`, `relatedTags[]`,
  `relatedScreens[]` (SCR-ID), `relatedWorkflows[]` (WF-ID).

**Entities**
- `name`, `domain` (из §3), `definition`, `businessMeaning`, `lifecycleRef`
  (ENTITY_STATES), отношения: `relatedEntities[]`, `modules[]`, `roles[]`,
  `glossaryTerms[]`, `articles[]`, `status` (confirmed / needs-validation).

**Tags**
- `name`, `type` (domain / role / module / entity), `description`, `locale`.

Метаданные для поиска/AI: `domain`, `roles`, `lifecycleState`, `sourceOfTruth`
(ссылка на raw-док), `confidence` (confirmed / needs-validation).

---

## 11. Open Questions

Терминологические расхождения (документируем оба варианта, не нормализуем):
1. **Freelancer (UI/design) = Service Provider (роуты/бэкенд)** — одна роль,
   два имени. Подтверждено; используем оба.
2. **Storekeeper (design) = «warehouse» (таблицы бэкенда)** — одно понятие.
3. **Order status:** текстовая цепочка вида Buyer ([GLOSSARY](GLOSSARY.md)) vs
   канонические числовые коды ([ENTITY_STATES](ENTITY_STATES.md)) — не конфликт;
   канон = ENTITY_STATES.
4. Источник статусов помечал секции «Box Status»(=Idea) и «Task Priority»
   (=Strategy) неверно — подтверждено пользователем, трактуем по смыслу.

Разрешено пользователем 2026-07-01 (трекер — [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md)):
5. ✅ **Order Item** — связка сущностей, принадлежащая Заказу (DM1).
6. ✅ **Inventory Item = Product** — карточка товара пользователя; статусы
   VACANT/…/UNLINKED = статусы этой карточки в связке с Supplier Card (DM2).
7. ✅ **Listing** — набор отчётов, не сущность (DM5).
8. ✅ **Super Box** — существует, контейнер из коробок (SB) (DM14).
11. ✅ **Account/User/Client/Sub-user** — Account = учётка пользователя,
    Client = только роль, User = platform-user (любая роль), Sub-user = член
    команды у любой роли (DM3).
12. ✅ **Research Product** — Product в статусах 0–15/200–205, не сущность;
    связь с Idea уточняется (DM4).
13. ✅ **Supplier Search Request** — мульти-ролевой процесс (Client сам или
    через Buyer); выделен отдельно (DM7).
14. ✅ **SKU/UPC/EAN** — атрибуты, не сущности (DM13).
15. ✅ **Voice of Customer** — аналитический срез (отчёт Voice: concession_rate,
    badge_status; Return Badge в NCX rating) (DM12).
16. ✅ **Support Ticket vs Feedback** — Ticket = запрос пользователя; Feedback =
    ответ Админа/модератора на запрос (DM9).
17. ✅ **Milestone** — глобальная сущность; крепится к Service Request и к Idea (DM11).
18. ✅ **Announcement** — карточка Услуги (объявление Service Provider) (DM16).
19. ✅ **Permission Preset** — жизненного цикла нет, просто набор (DM10).
21. ✅ **Brand Launch** — отдельный процесс (неск. Product Launch = Brand
    Launch); флоу/раздела пока нет, описание стратегии отсутствует (DM17).
+ **Parent↔Variation** — Variation это Product; Parent = связь/зависимость (DM18).

Остаются открытыми (**Needs validation**):
9. **Dashboard Widget** — есть ли конфигурируемые виджеты? (DM15 — без ответа)
10. **Connected App / Apps Marketplace** — функционал **в разработке** (DM6).
19b. **Batch lifecycle** — точные коды/переходы (DM8 — ответ позже).
20. **Отчёты** (ORDERS, INCOME, TRANSACTIONS, VOICE, FBA_INVENTORY и др.) —
    какие описывать как продуктовые (DM19 — уточняется).
+ **Research Product ↔ Idea** — характер связи (часть DM4, уточняется).

Тестовые данные: в листе логинов ([ENTITY_STATES](ENTITY_STATES.md)) e-mail
смещены относительно ролей — использовать только маппинг `CODE→ROLE`.

---

## Self-review

- **Confirmed entities:** приведены с источниками (Glossary / ENTITY_STATES /
  SCREEN_CATALOG / WORKFLOW_CATALOG / PERMISSIONS_MATRIX / localizations / raw
  data_filters).
- **Assumptions:** все спорные трактовки помечены **Needs validation** и
  продублированы в §11.
- **Terminology conflicts:** §11 п.1–4.
- **Unresolved:** §11 п.5–21.

> Документ оптимизирован на корректность, не на полноту. Меньший, но верный
> набор — предпочтительнее. При сомнении — см. Open Questions и уточнить.
