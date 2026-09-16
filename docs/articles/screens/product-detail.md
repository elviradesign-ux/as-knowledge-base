---
title: "Товар — карточка (детали)"
slug: product-detail
article_type: Screen Guide
section: Screens Reference
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Client, Admin]
roles: [Client, Admin]
modules: [Inventory, Product]
entities: [Product, ASIN, Variation, Supplier Card, Tag]
workflows: [WF-030]
related_screens: [SCR-121, SCR-120, SCR-M01]
related_entities: [Product, ASIN, Variation, Supplier Card]
related_articles: [001-product, 013-product-card, inventory-products]
seo_title: "Товар — карточка (детали): гайд по экрану Seller Exchange"
seo_description: "Гайд по экрану деталей товара в Seller Exchange: данные товара, вариации, поставщики, медиа и действия; как открыть и что можно сделать."
owner: TBD
last_updated: 2026-07-03
review_by: 2026-10-03
locales: [en, ru, zh, ua]
source_documents:
  - SCREEN_CATALOG.md (SCR-121, SCR-120)
  - GLOSSARY.md (Карточка продукта; Inventory — поля таблицы)
  - reference/modals.md (модалки товара)
  - localizations/*.tokens.json (actions_*)
  - figma-mcp/sources/mhtml/ (захват ProductView)
validation_status: "confirmed (визуальный источник — mhtml; капчур ProductView из контекста биржи, инвентарный контекст желателен)"
---

> **Гайд по экрану (ru-источник).** Описывает *действия* на экране. Понятие
> товара — в [Что такое товар](../foundations/001-product.md). Визуальный
> источник — mhtml-захват (см. ниже).

# Товар — карточка (детали)

## Кратко

Экран деталей открывает данные **одного товара**: идентификаторы, вариации,
поставщиков, медиа и финансовые показатели. Открывается из
[инвентаря](inventory-products.md) по клику на товар. Route:
`/inventory/products/:id` (`ProductView`, [SCR-121](../../SCREEN_CATALOG.md)).

## Кому и когда пригодится

- **Client** — посмотреть/отредактировать данные своего товара.
- **Admin** — то же в рамках надзора.

## Предварительные условия

- Роль Client или Admin.
- Товар существует в [инвентаре](inventory-products.md) (иначе открывать нечего).

## Элементы экрана

Экран сводит данные товара (полный список полей — в
[GLOSSARY → Inventory — поля таблицы](../../GLOSSARY.md), не дублируется):

- **Идентификаторы** — ASIN, FNSKU, баркод.
- **Основная информация** — бренд, категория, название, состояние.
- **Вариации** — связанные товары (родитель/вариация).
- **Поставщики** — привязанные карточки поставщика.
- **Медиа** — фото/изображения товара.
- **Финансы** — себестоимость (COG), комиссии, прибыль, ROI.

## Действия

Названия — из локализации (`actions_*`), EN / *RU*:

- **Add changes to the product** / *Внести изменения в продукт* — редактирование.
- **Add a variation** / *Добавить вариацию*, привязка — модалка `BindProductModal`.
- **Add barcode** / *Добавить баркод*, HS-код — модалка `BarHsCodeModal`.
- **Add a red flag icon** / *Добавить иконку красного флага* — пометить риск.
- **Add comment** / *Добавьте комментарий* — заметка к товару.
- Работа с себестоимостью — модалка `CogModal`; с поставщиком — `SupplierCardModal`,
  `SelectionSupplierModal`; с тегами — `TagsListModal`; медиа — `GalleryModal`.
- Создать заказ по товару — **To order** / *К заказу*
  (`CreateOrderModal`, [SCR-M01](../../SCREEN_CATALOG.md)).

Полный перечень модалок товара — в [reference/modals.md](../../reference/modals.md).

## Результат

- Изменения сохраняются в данных товара и видны в [инвентаре](inventory-products.md).
- Созданный заказ уходит в раздел заказов (см. [Что такое заказ](../foundations/003-order.md)).

## Смежные экраны

| Экран | Роль экрана |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Инвентарь — товары | Список, откуда открывается карточка |
| [SCR-M01](../../SCREEN_CATALOG.md) `CreateOrderModal` | Создание заказа по товару |

## Визуальные источники (mhtml)

Захваты — в `figma-mcp/sources/mhtml/` (light/dark, En/Uk):

- `Client-ProductsExchange-ProductDetail.*.mhtml` — экран `ProductView` (тот же
  компонент, что и `/inventory/products/:id`; контекст — биржа).
- `Client-Inventory.*.mhtml`, `Client.Inventory.ExpandedTiles.*.mhtml` — контекст,
  из которого открывается карточка.

> Желателен отдельный захват карточки товара из **инвентарного** контекста
> (`/inventory/products/:id`).

## Частые проблемы

| Симптом | Причина | Решение |
|---|---|---|
| Не открывается карточка | Товар удалён/нет доступа | Проверить наличие товара и права |
| Нет данных о продажах | Не подключён магазин Amazon | Подключить магазин (`/shops/my-shops`) |

## Связанные материалы

- Концепт: [Что такое товар](../foundations/001-product.md), [Карточка товара](../foundations/013-product-card.md)
- Экран-список: [Инвентарь — товары](inventory-products.md)
- Поля: [GLOSSARY](../../GLOSSARY.md); Модалки: [reference/modals.md](../../reference/modals.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Действия — из локализации (`actions_*`), не выдуманы.
- [x] Модалки — по [reference/modals.md](../../reference/modals.md).
- [x] Визуальный источник — mhtml-захват `ProductView` указан.
- [ ] Желателен инвентарный капчур карточки; ревью вторым человеком.
