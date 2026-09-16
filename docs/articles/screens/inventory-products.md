---
title: "Инвентарь — таблица товаров"
slug: inventory-products
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Admin]
roles: [Client, Admin]
modules: [Inventory]
entities: [Inventory, Product, Order, Product Idea]
workflows: [WF-030, WF-032, WF-035]
related_screens: [SCR-120, SCR-121, SCR-122, SCR-M01, SCR-M07]
related_entities: [Product, Order, Box, Product Idea]
related_articles: [002-inventory, 001-product, 003-order]
seo_title: "Инвентарь — таблица товаров: гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану Инвентарь в Seller Exchange: таблица товаров, пресеты и колонки, создание заказа и запуск товара, частые проблемы."
owner: TBD
created: 2026-07-01
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-120…122, SCR-M01, SCR-M07)
  - GLOSSARY.md (Inventory — поля таблицы; Фильтры данных; CustomDataGrid)
  - WORKFLOW_CATALOG.md (WF-030, WF-032, WF-035)
  - localizations/*.tokens.json (actions_*, info_*)
  - reference/modals.md
validation_status: confirmed
---

# Инвентарь — таблица товаров

## Кратко

**Инвентарь** — каталог товаров с аналитикой: единая таблица, где сведены
данные о запасах, продажах, финансах и рекламе по каждому товару (ASIN).
Отсюда пользователь создаёт заказы, запускает товары и настраивает
представление таблицы под свои задачи. Экран: `/inventory/products`
(`InventoryView`, № 300).

## Кому и когда пригодится

- **Client** — управляет собственным каталогом: следит за остатками,
  дозакупкой, создаёт заказы.
- **Admin** — те же возможности в рамках надзора за товарами клиентов.

Доступ по ролям — см. [PERMISSIONS_MATRIX](../../PERMISSIONS_MATRIX.md)
(Inventory: Client, Admin).

## Предварительные условия

- Роль Client или Admin.
- Подключён хотя бы один магазин Amazon (`/shops/my-shops`) — иначе таблица
  пуста. См. сценарий подключения магазина в
  [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md).

## Элементы экрана

### Таблица (CustomDataGrid)

Основная область — таблица товаров. Колонки соответствуют полям из раздела
**«Inventory — поля таблицы (Amazon FBA)»** в [GLOSSARY](../../GLOSSARY.md):
ASIN, Fnsku, Available, Reserved Quantity, Days Of Supply, Цена амазон,
Прибыль, Roi, Tacos и др. (~180 полей, сгруппированы: идентификация, запасы,
возраст запаса, продажи, финансы, реклама, рекомендации).

Ширина колонок токенизируется по значению (`col-width-100`, см.
[GLOSSARY](../../GLOSSARY.md) → CustomDataGrid).

### Пресеты (наборы колонок)

Состояние таблицы (набор и порядок колонок, фильтры) сохраняется в **пресет**.
Управление:
- **Add a preset** / *Добавить пресет* — создать новый пресет.
- **Save preset** / *Сохранить пресет* — сохранить изменения.
- **Save the state of the table to this preset** / *Сохранить состояние таблицы
  в этом пресете* — записать текущий вид в выбранный пресет.
- При изменении: тост *Active preset changed / Активный пресет изменён*.
- Удаление подтверждается: *Are you sure delete this preset? / Вы уверены, что
  хотите удалить этот пресет?*

### Управление колонками

- **Select column** / *Выбрать колонку*, **Add column before / after** /
  *Добавить колонку слева / справа*, **Delete column** / *Удалить колонку*.
- Кастомные вычисляемые колонки — через привязку колонок
  (см. `Obsidian Vault/wiki/ФУНКЦИОНАЛ/Column Binding.md`).

## Действия

Названия кнопок приведены точно по локализации (`actions_*`,
`figma-mcp/localizations/`), EN / *RU*.

### Добавление товара

1. **Add product** / *Добавить товар* — открывает выбор способа.
2. Варианты: **Add your product** / *Добавить свой товар*
   (`AddOwnProductModal`), **Add a product card** / *Добавить карточку товара*,
   **Add a list of ASIN** / *Добавьте список ASIN*.
3. Подтверждение создания: *Are you sure you want to create a product? / Вы
   уверены, что хотите создать продукт?*

> ⚠️ ASIN не может быть пустым: *ASIN cannot contain empty values / ASIN не
> может содержать пустые значения*.

### Создание заказа из инвентаря — WF-030

1. Отметьте строки нужных товаров чекбоксами.
2. Нажмите **To order** / *К заказу* — открывается модалка создания заказа
   (`CreateOrderModal`, [SCR-M01](../../SCREEN_CATALOG.md)).
3. Распределите товар по коробкам и подтвердите (см. сценарий WF-031).

Созданный заказ стартует со статуса `NEW` (или `FORMED` для отложенного) и
идёт по жизненному циклу до `SHIPPED` — коды в
[ENTITY_STATES](../../ENTITY_STATES.md) → «Статусы заказа».

Полный флоу — [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-030, WF-031).

### Запуск товара — WF-032

- **Add a idea** / *Добавить идею* — заводит идею в пайплайн запуска
  (`IdeaModal`, [SCR-M07](../../SCREEN_CATALOG.md)); далее товар проходит
  вкладки Product Launch (статусы New → On checking → … → Realized/Rejected,
  см. [ENTITY_STATES](../../ENTITY_STATES.md) → «Статусы идеи»).

### Прочие действия над строкой

- **Add to inventory** / *Добавить в инвентарь*, **Add to quick access** /
  *Добавить в быстрый доступ*.
- **Add Tag** / *Добавить тег*, **Add a new tag** / *Добавить новый тег*;
  массово — **Delete selected tags** / *Удалить выбранные теги*.
- **Add barcode** / *Добавить баркод*, HS-код — модалка `BarHsCodeModal`.
- **Add a red flag icon** / *Добавить иконку красного флага* — отметить риск
  (поле «Красные флаги», см. [GLOSSARY](../../GLOSSARY.md)).
- **Add comment** / *Добавьте комментарий* — заметка к товару.
- **Cancel order** / *Отменить заказ*, **Cancel selected orders** / *Отменить
  выбранные заказы*; массово по ASIN — **Delete selected ASINs** / *Удалить
  выбранные ASIN*.

Подтверждения (`info_*`): *Are you sure you want to remove the product?*,
*…delete ASIN?*, *…cancel the order?* — соответствующие RU-строки берутся из
локализации, не перефразируются.

### AI-анализ

Кнопка AI-ассистента (`AiAssistantModal`) запускает анализ данных по текущим
фильтрам таблицы (см. `wiki/ФУНКЦИОНАЛ/AI Analyzer.md`).

## Результат

- Товар отображается строкой в таблице с актуальными полями (Available,
  Days Of Supply, Прибыль и т.д.).
- Созданный заказ уходит в раздел [Orders](../../SCREEN_CATALOG.md) и цепочку
  обработки Buyer → Storekeeper (см. сквозной процесс в
  [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md); статусы заказа `NEW → … →
  IN_STOCK/SHIPPED` — в [ENTITY_STATES](../../ENTITY_STATES.md)).
- Сохранённый пресет доступен для повторного применения.

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-121](../../SCREEN_CATALOG.md) Товар — детали (`/inventory/products/:id`) | Карточка продукта, вариации, поставщики |
| [SCR-122](../../SCREEN_CATALOG.md) Инвентарь — отчёты (`/inventory/reports`) | Отчёты по листингам |
| [SCR-M01](../../SCREEN_CATALOG.md) `CreateOrderModal` | Создание заказа |
| [SCR-M07](../../SCREEN_CATALOG.md) `IdeaModal` | Запуск товара |

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Таблица пуста | Не подключён магазин Amazon | Подключить магазин в `/shops/my-shops` |
| Нельзя создать заказ | Не отмечены строки | Отметить товары чекбоксами перед **To order** |
| Не создаётся товар | Пустой ASIN | Заполнить ASIN (*ASIN cannot contain empty values*) |
| Пропали колонки | Применён другой пресет | Выбрать/пересохранить нужный пресет |

## Связанные материалы

- Экраны: [SCREEN_CATALOG](../../SCREEN_CATALOG.md) (SCR-120…122, SCR-M01, SCR-M07)
- Сценарии: [WORKFLOW_CATALOG](../../WORKFLOW_CATALOG.md) (WF-030, WF-031, WF-032, WF-035)
- Термины и поля: [GLOSSARY](../../GLOSSARY.md) (раздел «Inventory — поля таблицы»)
- Статусы (товар, заказ, идея): [ENTITY_STATES](../../ENTITY_STATES.md)
- Строки UI: `figma-mcp/localizations/*.tokens.json`
- Первоисточник: `Obsidian Vault/wiki/ФУНКЦИОНАЛ/Inventory.md`
