---
title: "Карта таблиц (CustomDataGrid)"
slug: tables
article_type: Internal Reference
section: Reference
status: reference
locale: ru
localization_status: ru-source
sync_source: figma-mcp/platform-routes.md (Platform tables)
last_updated: 2026-07-02
source_documents:
  - figma-mcp/platform-routes.md
  - GLOSSARY.md (CustomDataGrid, Фильтры данных)
validation_status: confirmed
---

> **Internal Reference (синхронизируется из `platform-routes.md`).** Где в
> продукте используется компонент таблицы **CustomDataGrid** (см.
> [GLOSSARY → CustomDataGrid](../GLOSSARY.md)). Полезно при написании
> Screen/Workflow-гайдов. Роль **Warehouse** в таблицах = **Storekeeper**.
>
> Механику фильтрации колонок см. [GLOSSARY → Фильтры данных](../GLOSSARY.md) и
> raw-доку `figma-mcp/docs/Data filters*.md`.

## Таблицы по ролям (views)

### Admin
- `user-permissions` (Права пользователей)
- `users/platform-users` (Пользователи платформы)
- `batches/sent-batches` (Отправленные партии)
- `batches/awaiting-batches` (Ожидающие партии)
- `exchange` (Обмен)
- `settings/general/tabs/destinations` (Настройки: Направления)
- `settings/general/tabs/milestones` (Настройки: Этапы)
- `settings/general/tabs/freelance` (Настройки: Фриланс)
- `settings/general/tabs/tags` (Настройки: Теги)
- `warehouse/boxes` (Склад: Коробки)
- `warehouse/tasks` (Склад: Задачи)
- `orders/my-orders` (Мои заказы)
- `inventory` (Инвентарь)

### Client
- `notifications/requests-notification` (Уведомления: Запросы)
- `notifications/orders-notification` (Уведомления: Заказы)
- `notifications/boxes-notification` (Уведомления: Коробки)
- `notifications/boxes-tariff-notification` (Уведомления: Тарифы коробок)
- `warehouse/in-stock-boxes` (Склад: Коробки на складе)
- `warehouse/tasks` (Склад: Задачи)
- `my-shops` (Мои магазины)
- `ideas` (Идеи)
- `batches/awaiting-batches` (Ожидающие партии)
- `batches/sent-batches` (Отправленные партии)
- `parsing-reports` (Отчёты парсинга)
- `exchanges/niche` (Обмен: Ниша)

### Buyer
- `orders/pending-orders` (Заказы: Ожидающие)
- `orders/my-orders` (Заказы: Мои заказы)
- `orders/free-orders` (Заказы: Свободные)
- `ideas` (Идеи)
- `suppliers` (Поставщики)
- `search-supplier` (Поиск поставщика)
- `products` (Продукты)

### Warehouse (Storekeeper)
- `my-warehouse` (Мой склад)
- `management` (Управление)
- `batches` (Партии)
- `tasks` (Задачи)

### Supervisor
- `ready-to-check` (Готовые к проверке)
- `settings` (Настройки)
- `products` (Продукты)

### Researcher
- `products` (Продукты)

### Freelancer
- `source-files` (Исходные файлы)

### Shared (общие для нескольких ролей)
- `profile` (Профиль) · `my-requests` (Мои запросы) · `another-user` (Другой
  пользователь) · `patch-noutes` (Патчи) · `vacant-requests` (Вакантные запросы) ·
  `my-proposals` (Мои предложения) · `reports` (Отчёты) ·
  `parsings/parsing-requests` (Запросы на парсинг) · `parsings/parsing-profile`
  (Профиль парсинга) · `support` (Поддержка) · `sub-users` (Подпользователи) ·
  `general-notifications` (Общие уведомления)

## Таблицы в модалках (components/modals)

- `batch-more-info-modal` (Подробная информация о партии)
- `service-modal` (Сервис)
- `create-service-modal` (Создание сервиса)
- `link-request-modal` (Ссылки на заявки)
- `report-modal` (Отчёт)
- `return-details-modal` (Детали возврата: Возвраты)
- `return-details-modal` (Детали возврата: Меры)
- `supplier-approximate-calculations-modal` (Расчёты поставщика)
- `move-box-to-batch-modal` (Перемещение коробки в партию)
- `receive-box-modal` (Получение коробки: Новые коробки)
- `supplier-card-modal` (Карточка поставщика: Связанные продукты)
- `edit-batch-modal` (Редактирование партии: список коробок)
- `edit-batch-modal` (Редактирование партии: коробки в партии)
- `supplier-modal` (Поставщик)
- `batch-info-modal` (Информация о партии)
- `product-data-modal` (Данные продукта)
- `product-and-batch-modal` (Продукт и партия)

## Самостоятельные таблицы (часть интерфейса)

- `table` (Список поставщиков)
- `table` (Коробки к заказу)
- `product/table` (Продукт: поставщик услуг)
- `table` (Информация по продукту)
