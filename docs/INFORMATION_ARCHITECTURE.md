# Information Architecture — карта разделов

> Полная карта разделов базы знаний Seller Exchange (внутр. **AmazonService /
> AS**). Определяет, куда что кладём. Принципы — в [MANIFESTO](MANIFESTO.md).
>
> Структура повторяет реальные модули продукта (из
> `wiki/ФУНКЦИОНАЛ/App Structure.md` и `platform-routes.md`).

## Верхнеуровневые разделы

```
Knowledge Base
├── 1. Getting Started        — вход, регистрация, интерфейс, роли за 5 минут
├── 2. Concepts               — сущности: карточка, заказ, коробка, партия…
├── 3. Workflows              — как выполнять задачи (по ролям)
├── 4. Screens Reference      — справочник по каждому экрану/модалке
├── 5. Roles & Access         — что кому доступно (RBAC)
├── 6. Modules                — функциональные разделы платформы (ниже)
├── 7. Integrations & Data    — магазины Amazon, парсинг, экспорт, API
├── 8. Design System          — токены, компоненты, CustomDataGrid
├── 9. Troubleshooting & FAQ  — типовые проблемы
└── 10. Release Notes         — патч-ноуты
```

## Раздел 6 — Modules (карта функционала)

Модули соответствуют пунктам меню и роутам платформы:

| Модуль | Роут (пример) | Роли-владельцы |
|---|---|---|
| Dashboard | `/dashboard` | Все (свой на роль) |
| Orders (заказы) | `/orders`, `/my-orders`, `/free-orders` | Client, Buyer, Admin |
| Inventory (инвентарь) | `/inventory` | Client, Admin |
| Product Card (карточка) | `/…/:id` → `ProductView` | Researcher, Buyer, Supervisor |
| Product Launch (идеи) | `/product-launch` | Client, Buyer |
| Product Exchange (биржа товаров) | `/product-exchange` | Client, Admin |
| Ready to check | `/ready-to-check` | Supervisor |
| Suppliers (поставщики) | `/suppliers`, `/supplier-search` | Buyer |
| Warehouse (склад) | `/warehouse`, `/my-warehouse` | Client, Storekeeper, Admin |
| Tasks (задачи) | `/tasks` | Storekeeper |
| Batches (партии) | `/batches`, `/my-batches` | Client, Storekeeper, Admin |
| Warehouse Management (тарифы) | `/warehouse-management` | Storekeeper |
| Freelance/Service Exchange | `/service-provider` | Client, Freelancer |
| Stores (магазины) | `/shops` | Client |
| Finances (финансы) | `/finances` | почти все |
| Users & Permissions | `/users`, `/user-permissions` | Все / Admin, Buyer |
| Messages (чат) | `/messages` | почти все |
| Notifications (уведомления) | `/notifications` | Client, Buyer, Storekeeper, Freelancer, Admin |
| Support (тикеты) | `/support` | Все |
| Parsing (парсинг) | `/parsing` | Admin |
| Settings (настройки) | `/settings` | Admin, Supervisor |
| Tools (инструменты) | `/tools` | Client, Admin |
| Profile / Localization / Version History | `/profile`, `/patch-notes` | Все |

Полное соответствие «модуль → экраны» — в [SCREEN_CATALOG](SCREEN_CATALOG.md);
«модуль → сценарии» — в [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md).

## Правила размещения (decision rules)

- **Термин** → [GLOSSARY](GLOSSARY.md), не в тело статьи.
- **Описание экрана/модалки** → раздел 4 / [SCREEN_CATALOG](SCREEN_CATALOG.md).
- **Пошаговая задача** → раздел 3 / [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md).
- **Кто что может** → раздел 5 / [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md).
- **Токен/компонент** → раздел 8 (Design System).
- **Код/статус сущности (enum)** → [ENTITY_STATES](ENTITY_STATES.md); в статьях
  и глоссарии ссылаемся, не дублируем.
- Если непонятно, куда класть — спроси (см. [CONTRIBUTING](CONTRIBUTING.md)).

## Naming & URL

- Файлы статей: `kebab-case.md`; переводы: `name.<lang>.md`.
- Каждая статья начинается с шапки из [ARTICLE_TEMPLATE](ARTICLE_TEMPLATE.md).
- Идентификаторы стабильны: экраны `SCR-###`/`SCR-M###`, сценарии `WF-###`.
- Глубина вложенности — максимум 3 уровня.

## Источники правды (raw)

База знаний строится поверх материалов проекта — их не редактируем через КБ:
- `Obsidian Vault/wiki/` — продуктовая wiki (47 страниц: функционал, роли,
  дизайн-система, анализ конкурентов, стратегия).
- `platform-routes.md` — роуты, компоненты, 117 модалок, таблицы CustomDataGrid.
- `platform-mockups-index.md`, `platform_tables_figma_mapping.md` — макеты и
  привязка к Figma.
- `figma-mcp/docs/Data filters *.md` — API `data_filters` (инженерная
  документация): фильтруемые колонки по таблицам и видимость данных по роли.
  В КБ вносим только продуктовую выжимку (глоссарий + data scoping в матрице).
