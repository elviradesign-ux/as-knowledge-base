# Permissions Matrix — роли и доступы

> Источник правды о ролях и доступах Seller Exchange (внутр. кодовое имя —
> **AmazonService / AS**). На роли отсюда ссылаются
> [SCREEN_CATALOG](SCREEN_CATALOG.md), [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md),
> поле `audience` в [ARTICLE_TEMPLATE](ARTICLE_TEMPLATE.md).
>
> Первоисточники: `Obsidian Vault/wiki/РОЛИ/Role Map.md`, `platform-routes.md`
> (реальные роуты и компоненты), `wiki/ФУНКЦИОНАЛ/AMAZONSERVICE.md`.

## Модель доступа

Платформа использует **role-based access control (RBAC)**. Каждая роль видит
свой набор пунктов меню, данных и действий. Дополнительно у пользователей есть
**саб-пользователи** и **пресеты разрешений** (модалки `PermissionsModal`,
`SinglePermissionModal`, `GroupPermissionModal`), которые уточняют доступ
внутри роли — настраиваются Admin/Buyer в разделе `/user-permissions`.

## Роли

Wiki фиксирует **8 продуктовых ролей**; в роутах приложения присутствуют ещё
служебные (`Moderator`, `Guest`). Имена местами расходятся между дизайном и
кодом — расхождения отмечены.

| CODE | Роль (design) | Роль в роутах | RU | Основная зона ответственности |
|---|---|---|---|---|
| 0 | Admin | `Admin` | Админ | Полный доступ, настройки, права, парсинг |
| 10 | Client | `Client` | Клиент | Конечный клиент: заказы, инвентарь, склад, аналитика |
| 20 | Supervisor | `Supervisor` | Супервайзер | Проверка карточек, верификация поставщиков, ASIN-чекер |
| 30 | Researcher | `Researcher` | Ресечер | Ресёрч товара, создание карточек |
| 35 | Freelancer | `Service Provider` ⚠️ | Фрилансер | Услуги для запусков на Amazon (биржа услуг) |
| 40 | Buyer | `Buyer` | Байер | Сорсинг товара, поставщики, обработка заказов |
| 45 | Storekeeper | `Storekeeper` | Сторкипер | Складские операции, коробки, партии, задачи |
| 50 | Candidate | — ⚠️ | Кандидат | Пайплайн найма (не определён в UI) |
| 60 | — | `Moderator` | Модератор | Служебная: патч-ноуты, пользователи, поддержка |
| — | — | `Guest` | Гость | Пустой набор роутов (нет доступа) |

> Коды ролей (`CODE`) — из [ENTITY_STATES](ENTITY_STATES.md) (бэкенд-enum).

> ⚠️ **Freelancer (design) = Service Provider (routes).** `Candidate` есть в
> Role Map, но собственных роутов не имеет. `Moderator`/`Guest` есть в роутах,
> но не описаны как продуктовые роли. Свести имена перед публикацией.

## Основной рабочий процесс (цепочка ролей)

```
Researcher   → создаёт карточки товара
   ↓
Supervisor   → проверяет/утверждает карточки, верифицирует поставщиков
   ↓
Buyer        → ищет поставщиков, заполняет данные, возвращает Supervisor
   ↓
Supervisor   → верифицирует данные поставщика, публикует на биржу
   ↓
Client       → покупает карточки с биржи, создаёт заказы
   ↓
Buyer        → обрабатывает заказы, ведёт оплаты поставщикам
   ↓
Storekeeper  → принимает коробки, распределяет, формирует партии
   ↓
(Storekeeper принял → Buyer получает уведомление «Ожидает подтверждения заказа»)
```
Freelancer работает независимо через [[Биржа услуг]]. Admin — полный надзор и
конфигурация.

## Матрица «меню → роль»

Обозначения: ✓ доступно · — нет доступа. Источник: Role Map.

| Пункт меню | Client | Researcher | Supervisor | Buyer | Storekeeper | Freelancer | Admin |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Dashboard | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Freelance/Service Exchange | ✓ | — | — | — | — | ✓ | — |
| Inventory | ✓ | — | — | — | — | — | ✓ |
| Products (research) | — | ✓ | — | ✓ | — | — | — |
| Product Launch | ✓ | — | — | ✓ | — | — | — |
| Product Exchange | ✓ | — | — | — | — | — | ✓ |
| Orders | ✓ | — | — | ✓ | — | — | ✓ |
| Warehouse | ✓ | — | — | — | ✓ | — | ✓ |
| Batches | ✓ | — | — | — | ✓ | — | ✓ |
| Ready to check | — | — | ✓ | — | — | — | — |
| Suppliers | — | — | — | ✓ | — | — | — |
| Tasks | — | — | — | — | ✓ | — | — |
| Warehouse Management | — | — | — | — | ✓ | — | — |
| Stores / Shops | ✓ | — | — | — | — | — | — |
| Users | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Permissions | — | — | — | ✓ | — | — | ✓ |
| Finances | ✓ | — | ✓ | ✓ | ✓ | ✓ | ✓ |
| Notifications | ✓ | — | — | ✓ | ✓ | ✓ | ✓ |
| Messages | ✓ | — | ✓ | ✓ | ✓ | ✓ | ✓ |
| Support | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Settings | — | — | ✓ | — | — | — | ✓ |
| Parsing | — | — | — | — | — | — | ✓ |
| Profile / Version History / Localization / Theme | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

> Расхождение по Finances: Role Map отмечает Client=✓; матрица AMAZONSERVICE.md
> совпадает. Users для Admin в Role Map отмечен ✓, но в роутах Admin работает
> с под-разделами `/users/platform-users` и `/users/sub-users` — проверить.

## Что видит каждая роль (по роутам)

- **Admin** — `/dashboard`, `/product-exchange`, `/inventory`, `/orders`,
  `/warehouse`, `/batches`, `/finances`, `/users` (+platform-users, sub-users),
  `/user-permissions`, `/parsing`, `/settings` (general, dynamic-fields,
  dynamic-translations, onboarding), `/tools`, `/support`, `/messages`.
- **Buyer** — `/free-orders`, `/pending-orders`, `/suppliers`, `/my-orders`
  (8 статусных вкладок), `/my-products`, `/product-launch`, `/supplier-search`
  (from-supervisor / from-client), `/finances`, `/notifications`.
- **Client** — `/service-provider` (биржа услуг, мои запросы), `/inventory`
  (products, reports), `/product-launch` (8 вкладок), `/product-exchange`
  (products, supplier, niche), `/orders` (my-orders, pending-orders),
  `/warehouse` (in-stock, tasks), `/batches`, `/shops` (my-shops,
  parsing-reports), `/finances`, `/notifications` (5 вкладок), `/tools`.
- **Supervisor** — `/ready-to-check` (from-researcher / from-client),
  `/my-products`, `/settings` (ASIN-чекер).
- **Researcher** — `/dashboard`, `/my-products`.
- **Storekeeper** — `/tasks` (new, my, completed, canceled), `/my-warehouse`,
  `/my-batches` (awaiting-send, sent), `/warehouse-management`, `/finances`.
- **Service Provider (Freelancer)** — `/service-provider` (vacant-requests,
  my-proposals, all-proposals, source-files, my-services), `/finances`,
  `/notifications` (freelance).
- **Moderator** — `/patch-notes`, `/users`, `/support`, `/messages`.
- **Guest** — роутов нет.

Общие для всех: `/profile`, `/support`, `/messages`.

## Видимость данных по роли (data scoping)

Доступ к пункту меню — не то же, что доступ к записям. Внутри одного
представления бэкенд ограничивает, **какие записи** видит роль: к запросу
добавляется WHERE по роли и правам (эндпоинт `data_filters` и пагинация,
см. [[Фильтры данных]] в [GLOSSARY](GLOSSARY.md)).

Принципы:
- Представление привязано к владельцу записи: Client — свои
  (`createdById`/`clientId`), Buyer — взятые в работу (`buyerId`),
  Supervisor — проверяемые (`checkedById`), Storekeeper — свои
  (`storekeeperId`).
- «Свободные»/«вакантные» списки показывают неназначенные записи: свободные
  заказы Buyer — `status=[readyToProcess, formed], buyerId=null`; карточки на
  проверку Supervisor — `status=[5,10,35], checkedById=null`.
- **Саб-пользователь** видит только разрешённые ему продукты/магазины; при
  отсутствии доступа — ошибка «You don't have permission to the product/shop».
- Admin/Moderator по многим представлениям видят все записи.

Представительные примеры (view → область видимости):

| Представление (endpoint) | Роль | Область |
|---|---|---|
| `clients/pag/orders` | Client | свои заказы (`createdById`) |
| `buyers/orders/pag/my` | Buyer | заказы в работе (`buyerId`) |
| `buyers/orders/vac/pag` | Buyer | свободные (`status readyToProcess/formed`, VACANT) |
| `supervisors/products/vac` | Supervisor | на проверку (`status 5/10/35`, не назначено) |
| `researchers/products` | Researcher | свои неоплаченные (`createdById`, `paidAt=null`) |
| `storekeepers/pag/boxes` | Storekeeper | свои коробки на складе |
| `clients/suppliers_exchange` | Client | опубликованные (`status PUBLISHED`) |

> Полная карта из 71 представления (`endpointFiltersMap`) — в первоисточнике
> `figma-mcp/docs/Data filters (01.04.26)*.md`. Здесь — принцип и примеры,
> весь список не дублируем. Коды статусов — в [ENTITY_STATES](ENTITY_STATES.md).

## Правила ведения

- Любое изменение доступа отражается сначала здесь, потом в статьях.
- Новый экран/фича добавляется строкой в матрицу при создании.
- Значения ✓/— сверяются с `platform-routes.md` и Role Map.
