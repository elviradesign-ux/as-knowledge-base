---
title: "Роуты по ролям"
slug: routes-by-role
article_type: Internal Reference
section: Reference
status: reference
locale: ru
localization_status: ru-source
sync_source: figma-mcp/platform-routes.md (Routes by roles)
last_updated: 2026-07-02
source_documents:
  - figma-mcp/platform-routes.md
  - SCREEN_CATALOG.md
validation_status: confirmed
---

> **Internal Reference (синхронизируется из `platform-routes.md`).** Полный
> список роутов приложения по ролям. Канонический слой экранов КБ —
> [SCREEN_CATALOG](../SCREEN_CATALOG.md). Расхождения имён ролей UI↔бэкенд:
> **Service Provider** = роль Freelancer; таблицы склада относятся к роли
> **Storekeeper**.

## Admin

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Биржа товаров | `/product-exchange` | `ExchangeView` |
| Биржа товаров — детали | `/product-exchange/:id` | `ProductView` |
| Инвентарь | `/inventory` | `InventoryView` |
| Инвентарь — детали | `/inventory/:id` | `ProductView` |
| Заказы | `/orders` | `MyOrdersView` |
| Заказы — детали | `/orders/:id` | `OrderView` |
| Склад | `/warehouse` | `CategoryRootView` |
| Склад — задачи | `/warehouse/tasks` | `TasksView` |
| Склад — коробки | `/warehouse/boxes` | `BoxesView` |
| Партии | `/batches` | `CategoryRootView` |
| Партии — ожидающие отправки | `/batches/awaiting-send` | `AwaitingBatchesView` |
| Партии — отправленные | `/batches/sent-batches` | `SentBatchesView` |
| Патч-ноуты | `/patch-notes` | `PatchNoutesView` |
| Финансы | `/finances` | `FinancesViewSync` |
| Пользователи | `/users` | `CategoryRootView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Пользователи платформы | `/users/platform-users` | `PlatformUsersView` |
| Пользователи платформы — детали | `/users/platform-users/:id` | `UserView` |
| Саб-пользователи | `/users/sub-users` | `SubUsersView` |
| Права пользователей | `/user-permissions` | `UserPermissionsView` |
| Парсинг | `/parsing` | `CategoryRootView` |
| Парсинг — профили | `/parsing/profiles` | `ParsingProfileView` |
| Парсинг — запросы | `/parsing/requests` | `ParsingRequestsView` |
| Настройки | `/settings` | `CategoryRootView` |
| Настройки — общие | `/settings/general` | `GeneralSettingsView` |
| Настройки — динамические поля | `/settings/dynamic-fields` | `SettingsTabsView` |
| Настройки — динамические переводы | `/settings/dynamic-translations` | `DynamicTranslationsView` |
| Настройки — онбординг | `/settings/onboarding` | `OnboardingView` |
| Инструменты | `/tools` | `ToolsView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Buyer

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Свободные заказы | `/free-orders` | `FreeOrdersView` |
| Ожидающие заказы | `/pending-orders` | `PendingOrdersView` |
| Поставщики | `/suppliers` | `SuppliersView` |
| Поставщики — детали | `/suppliers/:id` | `SuppliersView` |
| Мои заказы | `/my-orders` | `CategoryRootView` |
| Мои заказы — все | `/my-orders/all` | `MyOrdersView` |
| Мои заказы — неоплаченные | `/my-orders/not-paid` | `MyOrdersView` |
| Мои заказы — готовы к оплате | `/my-orders/ready-for-payment` | `MyOrdersView` |
| Мои заказы — частично оплаченные | `/my-orders/partially-paid` | `MyOrdersView` |
| Мои заказы — нужен трек-номер | `/my-orders/need-track-number` | `MyOrdersView` |
| Мои заказы — входящие | `/my-orders/inbound` | `MyOrdersView` |
| Мои заказы — требуют подтверждения | `/my-orders/confirmation-required` | `MyOrdersView` |
| Мои заказы — закрытые и отменённые | `/my-orders/closed-and-canceled` | `MyOrdersView` |
| Мои товары | `/my-products` | `ProductsView` |
| Мои товары — детали | `/my-products/:id` | `ProductView` |
| Запуск товаров | `/product-launch` | `IdeasView` |
| Поиск поставщиков | `/supplier-search` | `CategoryRootView` |
| Поиск поставщиков — от супервайзера | `/supplier-search/from-the-supervisor` | `SearchSupplierView` |
| Поиск поставщиков — от супервайзера (детали) | `/supplier-search/from-the-supervisor/:id` | `ProductView` |
| Поиск поставщиков — от клиента | `/supplier-search/from-the-client` | `SearchSupplierView` |
| Поиск поставщиков — от клиента (детали) | `/supplier-search/from-the-client/:id` | `ProductView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Финансы | `/finances` | `FinancesViewSync` |
| Уведомления | `/notifications` | `GeneralNotificationsView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Client

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Сервис-провайдер | `/service-provider` | `CategoryRootView` |
| Биржа услуг | `/service-provider/service-exchange` | `ServiceExchangeView` |
| Мои запросы | `/service-provider/my-requests` | `MyRequestsView` |
| Мои запросы — детали | `/service-provider/my-requests/:id` | `RequestView` |
| Инвентарь | `/inventory` | `CategoryRootView` |
| Инвентарь — товары | `/inventory/products` | `InventoryView` |
| Инвентарь — товары (детали) | `/inventory/products/:id` | `ProductView` |
| Инвентарь — отчёты | `/inventory/reports` | `ReportsViewDynamic` |
| Запуск товаров | `/product-launch` | `CategoryRootView` |
| Запуск товаров — все | `/product-launch/all` | `IdeasViewDynamic` |
| Запуск товаров — новые идеи | `/product-launch/new-ideas` | `IdeasViewDynamic` |
| Запуск товаров — на проверке | `/product-launch/on-checking` | `IdeasViewDynamic` |
| Запуск товаров — поиск поставщика | `/product-launch/supplier-search` | `IdeasViewDynamic` |
| Запуск товаров — создание карточки | `/product-launch/create-card` | `IdeasViewDynamic` |
| Запуск товаров — добавление ASIN | `/product-launch/adding-asin` | `IdeasViewDynamic` |
| Запуск товаров — отклонённые и закрытые | `/product-launch/rejected-and-closed` | `IdeasViewDynamic` |
| Запуск товаров — реализованные | `/product-launch/realized-ideas` | `IdeasViewDynamic` |
| Биржа товаров | `/product-exchange` | `CategoryRootView` |
| Биржа товаров — оптовые товары | `/product-exchange/products` | `WholesaleView` |
| Биржа товаров — поставщик | `/product-exchange/products/supplier` | `SupplierView` |
| Биржа товаров — ниша | `/product-exchange/niche` | `NicheView` |
| Заказы | `/orders` | `CategoryRootView` |
| Мои заказы | `/orders/my-orders` | `MyOrdersViewAsync` |
| Мои заказы — детали | `/orders/my-orders/:id` | `ClientOrderView` |
| Ожидающие заказы | `/orders/pending-orders` | `MyOrdersViewAsync` |
| Ожидающие заказы — детали | `/orders/pending-orders/:id` | `ClientOrderView` |
| Склад | `/warehouse` | `CategoryRootView` |
| Склад — на складе | `/warehouse/in-stock` | `InStockBoxesView` |
| Склад — задачи | `/warehouse/tasks` | `TasksView` |
| Партии | `/batches` | `CategoryRootView` |
| Партии — ожидающие отправки | `/batches/awaiting-send` | `AwaitingBatchesView` |
| Партии — отправленные | `/batches/sent-batches` | `SentBatchesView` |
| Партии — архив | `/batches/sent-batches/archive` | `SentBatchesView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Магазины | `/shops` | `CategoryRootView` |
| Мои магазины | `/shops/my-shops` | `MyShopsView` |
| Отчёты парсинга | `/shops/parsing-reports` | `ParsingReports` |
| Финансы | `/finances` | `FinancesViewSync` |
| Уведомления | `/notifications` | `CategoryRootView` |
| Уведомления — по заказам | `/notifications/on-orders` | `OrdersNotificationView` |
| Уведомления — по коробкам | `/notifications/on-boxes` | `BoxesNotificationsView` |
| Уведомления — по тарифам коробок | `/notifications/on-boxes-tariffs` | `BoxesTariffNotificationView` |
| Уведомления — сообщения по запросам | `/notifications/request-messages` | `RequestsNotificationView` |
| Уведомления — общие | `/notifications/general` | `GeneralNotificationsView` |
| Поддержка | `/support` | `SupportView` |
| Инструменты | `/tools` | `ToolsView` |
| Сообщения | `/messages` | `MessagesView` |

## Moderator

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Патч-ноуты | `/patch-notes` | `PatchNoutesView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Researcher

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Мои товары | `/my-products` | `ProductsView` |
| Мои товары — детали | `/my-products/:id` | `ProductView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Service Provider (роль Freelancer)

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Сервис-провайдер | `/service-provider` | `CategoryRootView` |
| Вакантные запросы | `/service-provider/vacant-requests` | `VacantRequestsView` |
| Вакантные запросы — детали | `/service-provider/vacant-requests/:id` | `RequestView` |
| Мои предложения | `/service-provider/my-proposals` | `MyProposalsView` |
| Мои предложения — детали | `/service-provider/my-proposals/:id` | `RequestView` |
| Все предложения | `/service-provider/all-proposals` | `AllProposalsView` |
| Исходные файлы | `/service-provider/source-files` | `SourceFilesView` |
| Мои услуги | `/service-provider/my-services` | `MyServicesView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Финансы | `/finances` | `FinancesViewSync` |
| Уведомления | `/notifications` | `CategoryRootView` |
| Уведомления — фриланс | `/notifications/freelance-notifications` | `RequestsNotificationView` |
| Уведомления — общие | `/notifications/general` | `GeneralNotificationsView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Storekeeper

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Задачи | `/tasks` | `CategoryRootView` |
| Задачи — новые | `/tasks/new-tasks` | `VacantTasksView` |
| Задачи — мои | `/tasks/my-tasks` | `MyTasksView` |
| Задачи — выполненные | `/tasks/completed-tasks` | `CompletedTasksView` |
| Задачи — отменённые | `/tasks/canceled-tasks` | `CanceledTasksView` |
| Мой склад | `/my-warehouse` | `MyWarehouseView` |
| Мои партии | `/my-batches` | `CategoryRootView` |
| Партии — ожидающие отправки | `/my-batches/awaiting-send` | `AwaitingBatchesView` |
| Партии — отправленные | `/my-batches/sent-batches` | `SentBatchesView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Финансы | `/finances` | `FinancesViewSync` |
| Управление складом | `/warehouse-management` | `WarehouseManagementView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Supervisor

| Место | Путь | Компонент |
|---|---|---|
| Профиль | `/profile` | `ProfileView` |
| Дашборд | `/dashboard` | `DashboardView` |
| Готовые к проверке | `/ready-to-check` | `CategoryRootView` |
| Готовые к проверке — от ресёрчера | `/ready-to-check/from-the-researcher` | `ReadyToCheckView` |
| Готовые к проверке — от ресёрчера (детали) | `/ready-to-check/from-the-researcher/:id` | `ProductView` |
| Готовые к проверке — от клиента | `/ready-to-check/from-the-client` | `ReadyToCheckView` |
| Готовые к проверке — от клиента (детали) | `/ready-to-check/from-the-client/:id` | `ProductView` |
| Мои товары | `/my-products` | `ProductsView` |
| Мои товары — детали | `/my-products/:id` | `ProductView` |
| Пользователи | `/users` | `SubUsersView` |
| Пользователи — детали | `/users/:id` | `AnotherUserView` |
| Финансы | `/finances` | `FinancesViewSync` |
| Настройки | `/settings` | `SettingsView` |
| Поддержка | `/support` | `SupportView` |
| Сообщения | `/messages` | `MessagesView` |

## Guest

Роль Guest не имеет доступных роутов (пустой массив).
