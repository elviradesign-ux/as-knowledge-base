# Screen Catalog — все экраны платформы

> Реестр экранов Seller Exchange (внутр. **AmazonService / AS**). Один экран —
> одна статья по [ARTICLE_TEMPLATE](ARTICLE_TEMPLATE.md). На ID ссылаются
> сценарии [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md) и матрица
> [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md).
>
> Первоисточники: `platform-routes.md` (роуты + компоненты Vue-приложения),
> `wiki/ФУНКЦИОНАЛ/App Structure.md` (номера экранов), макеты в
> `Obsidian Vault/ФУНКЦИОНАЛ/*`.

## Как читать

- **Route** — путь в приложении, **Component** — компонент из `platform-routes.md`.
- **#** — номер экрана из App Structure (для сверки с Figma).
- **Доступ** — роли из [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md).

## Аутентификация

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-001 | Логин | `/login` | — | 001 | Все |
| SCR-002 | Регистрация | `/registration` | — | 002 | Все |

## Общие (все роли)

| ID | Экран | Route | Component | Доступ |
|---|---|---|---|---|
| SCR-010 | Профиль | `/profile` | `ProfileView` | Все |
| SCR-011 | Дашборд | `/dashboard` | `DashboardView` | Все (свой дэшборд на роль: 106–112) |
| SCR-012 | Финансы | `/finances` | `FinancesViewSync` | Client, Supervisor, Buyer, Storekeeper, Freelancer, Admin |
| SCR-013 | Уведомления | `/notifications` | `GeneralNotificationsView` / `CategoryRootView` | Client, Buyer, Storekeeper, Freelancer, Admin |
| SCR-014 | Сообщения (чат) | `/messages` | `MessagesView` | Все, кроме Researcher |
| SCR-015 | Поддержка (тикеты) | `/support` | `SupportView` | Все |
| SCR-016 | Пользователи | `/users` | `SubUsersView` / `CategoryRootView` | Все |
| SCR-017 | Пользователь — детали | `/users/:id` | `AnotherUserView` | Все |
| SCR-018 | Патч-ноуты | `/patch-notes` | `PatchNoutesView` | Admin, Moderator |
| SCR-019 | Инструменты | `/tools` | `ToolsView` | Client, Admin |

## Orders (заказы)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-100 | Мои заказы (Client) | `/orders/my-orders` | `MyOrdersViewAsync` | 600 | Client |
| SCR-101 | Заказ — детали (Client) | `/orders/my-orders/:id` | `ClientOrderView` | — | Client |
| SCR-102 | Ожидающие заказы (Client) | `/orders/pending-orders` | `MyOrdersViewAsync` | — | Client |
| SCR-103 | Мои заказы (Buyer, 8 вкладок) | `/my-orders/*` | `MyOrdersView` | 7000 | Buyer |
| SCR-104 | Заказ — детали (Buyer) | `/my-orders/:id` | — | 7001 | Buyer |
| SCR-105 | Свободные заказы (Buyer) | `/free-orders` | `FreeOrdersView` | 5001 | Buyer |
| SCR-106 | Ожидающие заказы (Buyer) | `/pending-orders` | `PendingOrdersView` | — | Buyer |
| SCR-107 | Заказы (Admin) | `/orders` → `/orders/:id` | `MyOrdersView` / `OrderView` | — | Admin |

Вкладки Buyer `/my-orders/*`: all, not-paid, ready-for-payment, partially-paid,
need-track-number, inbound, confirmation-required, closed-and-canceled.

## Inventory & Product

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-120 | Инвентарь — товары | `/inventory/products` | `InventoryView` | 300 | Client, Admin |
| SCR-121 | Товар — детали | `/inventory/products/:id` | `ProductView` | — | Client, Admin |
| SCR-122 | Инвентарь — отчёты | `/inventory/reports` | `ReportsViewDynamic` | — | Client |
| SCR-123 | Мои товары | `/my-products` | `ProductsView` | — | Buyer, Researcher, Supervisor |
| SCR-124 | Карточка продукта (ASIN) | — | `ProductView` | 1110/1700/1900 | по роли |

## Product Launch (идеи)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-140 | Запуск товаров — все | `/product-launch/all` | `IdeasViewDynamic` | 400 | Client |
| SCR-141 | Новые идеи | `/product-launch/new-ideas` | `IdeasViewDynamic` | — | Client |
| SCR-142 | На проверке | `/product-launch/on-checking` | `IdeasViewDynamic` | — | Client |
| SCR-143 | Поиск поставщика | `/product-launch/supplier-search` | `IdeasViewDynamic` | — | Client |
| SCR-144 | Создание карточки | `/product-launch/create-card` | `IdeasViewDynamic` | — | Client |
| SCR-145 | Отклонённые и закрытые | `/product-launch/rejected-and-closed` | `IdeasViewDynamic` | — | Client |
| SCR-146 | Запуск товаров (Buyer) | `/product-launch` | `IdeasView` | — | Buyer |

## Product Exchange (биржа товаров)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-160 | Биржа — оптовые товары | `/product-exchange/products` | `WholesaleView` | 500 | Client, Admin |
| SCR-161 | Биржа — поставщик | `/product-exchange/products/supplier` | `SupplierView` | — | Client |
| SCR-162 | Биржа — ниша | `/product-exchange/niche` | `NicheView` | — | Client |
| SCR-163 | Товар — детали | `/product-exchange/:id` | `ProductView` | — | Admin |

## Ready to check (Supervisor)

| ID | Экран | Route | Component | Доступ |
|---|---|---|---|---|
| SCR-180 | Готовые к проверке — от ресёрчера | `/ready-to-check/from-the-researcher` | `ReadyToCheckView` | Supervisor |
| SCR-181 | Готовые к проверке — от клиента | `/ready-to-check/from-the-client` | `ReadyToCheckView` | Supervisor |

## Suppliers / Supplier search (Buyer)

| ID | Экран | Route | Component | Доступ |
|---|---|---|---|---|
| SCR-190 | Поставщики | `/suppliers` | `SuppliersView` | Buyer |
| SCR-191 | Поиск поставщиков — от супервайзера | `/supplier-search/from-the-supervisor` | `SearchSupplierView` | Buyer |
| SCR-192 | Поиск поставщиков — от клиента | `/supplier-search/from-the-client` | `SearchSupplierView` | Buyer |

## Warehouse (склад)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-200 | Склад — коробки на складе (Client) | `/warehouse/in-stock` | `InStockBoxesView` | 700 | Client |
| SCR-201 | Склад — задачи (Client) | `/warehouse/tasks` | `TasksView` | — | Client |
| SCR-202 | Мой склад (Storekeeper) | `/my-warehouse` | `MyWarehouseView` | 1330 | Storekeeper |
| SCR-203 | Управление складом (тарифы/адреса) | `/warehouse-management` | `WarehouseManagementView` | 1380 | Storekeeper |
| SCR-204 | Склад — коробки (Admin) | `/warehouse/boxes` | `BoxesView` | — | Admin |
| SCR-205 | Склад — задачи (Admin) | `/warehouse/tasks` | `TasksView` | — | Admin |

## Tasks (Storekeeper)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-220 | Задачи — новые | `/tasks/new-tasks` | `VacantTasksView` | 1280 | Storekeeper |
| SCR-221 | Задачи — мои | `/tasks/my-tasks` | `MyTasksView` | — | Storekeeper |
| SCR-222 | Задачи — выполненные | `/tasks/completed-tasks` | `CompletedTasksView` | — | Storekeeper |
| SCR-223 | Задачи — отменённые | `/tasks/canceled-tasks` | `CanceledTasksView` | — | Storekeeper |

## Batches (партии)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-240 | Партии — ожидающие отправки | `/batches/awaiting-send` | `AwaitingBatchesView` | 1220 | Client, Storekeeper, Admin |
| SCR-241 | Партии — отправленные | `/batches/sent-batches` | `SentBatchesView` | — | Client, Storekeeper, Admin |
| SCR-242 | Партии — архив | `/batches/sent-batches/archive` | `SentBatchesView` | — | Client |

## Freelance / Service Exchange

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-260 | Биржа услуг (Client) | `/service-provider/service-exchange` | `ServiceExchangeView` | 200 | Client |
| SCR-261 | Мои запросы (Client) | `/service-provider/my-requests` | `MyRequestsView` | — | Client |
| SCR-262 | Вакантные запросы (Freelancer) | `/service-provider/vacant-requests` | `VacantRequestsView` | 250 | Freelancer |
| SCR-263 | Мои предложения (Freelancer) | `/service-provider/my-proposals` | `MyProposalsView` | — | Freelancer |
| SCR-264 | Все предложения (Freelancer) | `/service-provider/all-proposals` | `AllProposalsView` | — | Freelancer |
| SCR-265 | Мои услуги (Freelancer) | `/service-provider/my-services` | `MyServicesView` | — | Freelancer |
| SCR-266 | Исходные файлы (Freelancer) | `/service-provider/source-files` | `SourceFilesView` | — | Freelancer |

## Stores / Shops (Client)

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-280 | Мои магазины | `/shops/my-shops` | `MyShopsView` | 900 | Client |
| SCR-281 | Отчёты парсинга | `/shops/parsing-reports` | `ParsingReports` | — | Client |

## Admin-only

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-300 | Пользователи платформы | `/users/platform-users` | `PlatformUsersView` | — | Admin |
| SCR-301 | Саб-пользователи | `/users/sub-users` | `SubUsersView` | — | Admin |
| SCR-302 | Права пользователей | `/user-permissions` | `UserPermissionsView` | 12000 | Admin |
| SCR-303 | Парсинг — профили | `/parsing/profiles` | `ParsingProfileView` | 13000 | Admin |
| SCR-304 | Парсинг — запросы | `/parsing/requests` | `ParsingRequestsView` | — | Admin |
| SCR-305 | Настройки — общие | `/settings/general` | `GeneralSettingsView` | 14000 | Admin |
| SCR-306 | Настройки — динамические поля | `/settings/dynamic-fields` | `SettingsTabsView` | — | Admin |
| SCR-307 | Настройки — динамические переводы | `/settings/dynamic-translations` | `DynamicTranslationsView` | — | Admin |
| SCR-308 | Настройки — онбординг | `/settings/onboarding` | `OnboardingView` | — | Admin |

## Supervisor-only

| ID | Экран | Route | Component | # | Доступ |
|---|---|---|---|---|---|
| SCR-320 | Настройки — ASIN-чекер | `/settings` | `SettingsView` | 1600 | Supervisor |

## Модальные окна

Платформа содержит **117 модальных окон** (`CreateOrderModal`, `EditOrderModal`,
`CreateBoxModal`, `PermissionsModal`, `IdeaModal`, `SupplierModal`,
`BatchInfoModal` и др.). Полный реестр с точками вызова — в
[reference/modals.md](reference/modals.md) (синхронизируется из
`platform-routes.md`). Каждая значимая модалка при документировании получает свой
`SCR-M###` и статью — ID минтуются здесь. Полные роуты по ролям —
[reference/routes-by-role.md](reference/routes-by-role.md); карта таблиц —
[reference/tables.md](reference/tables.md).

Ключевые:

| ID | Модалка (component) | Точки вызова |
|---|---|---|
| SCR-M01 | Создание заказа (`CreateOrderModal`) | Client → Инвентарь, Идеи, Заказы, Биржа→Ниша, Склад→Коробки |
| SCR-M02 | Новый заказ (`NewOderModal`) | Внутри Модалки создания заказа |
| SCR-M03 | Редактирование заказа (`EditOrderModal`) | Buyer → Мои заказы, Отложенные заказы |
| SCR-M04 | Создание коробки (`CreateBoxModal`) | Модалка редактирования заказа |
| SCR-M05 | Группировка коробок (`GroupingBoxesModal`) | Client → Склад→Коробки; Склад→Мой склад |
| SCR-M06 | Разрешения (`PermissionsModal`) | Субпользователи; Admin → Редактирование пользователя |
| SCR-M07 | Идея (`IdeaModal`) | Client/Buyer → Идеи; Client → Инвентарь; Уведомления |
| SCR-M08 | Дедлайн (`DeadlineModal`) | Модалка создания заказа |

## Правила ведения

- ID стабилен, не переиспользуется.
- Экран без связанного сценария помечается `(TODO: workflow)`.
- Названия элементов согласованы с [GLOSSARY](GLOSSARY.md).
- Route/Component сверяются с `platform-routes.md`.
