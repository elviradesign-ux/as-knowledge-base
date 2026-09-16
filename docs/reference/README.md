# Reference — технический справочный слой

> **Internal Reference.** Навигационные срезы для команды (dev / writers): роуты
> по ролям, реестр модалок, карта таблиц. Это **производный** слой,
> синхронизируемый из raw-источника `figma-mcp/platform-routes.md` — **не** новый
> источник правды.
>
> Принцип «один факт — одно место» ([CONTRIBUTING](../CONTRIBUTING.md),
> [DOCUMENTATION_PRODUCTION_PIPELINE §2](../DOCUMENTATION_PRODUCTION_PIPELINE.md)):
> канонический слой экранов КБ — [SCREEN_CATALOG](../SCREEN_CATALOG.md)
> (`SCR-###` / `SCR-M###`). Этот справочник его **дополняет** (полные роуты,
> все 117 модалок, таблицы), а не заменяет.

## Файлы

| Файл | Что внутри | Источник |
|---|---|---|
| [routes-by-role.md](routes-by-role.md) | Все роуты приложения по ролям (путь + компонент) | `platform-routes.md` → Routes by roles |
| [modals.md](modals.md) | Реестр 117 модалок (компонент, назначение, точки вызова, `SCR-M`) | `platform-routes.md` → Platform modals |
| [tables.md](tables.md) | Карта CustomDataGrid (таблицы по ролям, в модалках, standalone) | `platform-routes.md` → Platform tables |

## Как пользоваться

- **Writers** — искать экран/модалку/таблицу при написании Screen/Workflow-гайдов
  и брать стабильный идентификатор (route/component; `SCR-M###` — из
  [SCREEN_CATALOG](../SCREEN_CATALOG.md)).
- **Dev** — сверять роуты и компоненты.
- **Стабильные ID модалок** (`SCR-M###`) минтуются в
  [SCREEN_CATALOG](../SCREEN_CATALOG.md) по мере документирования; здесь — полный
  инвентарь по имени компонента.

## Правила ведения (важно)

- **Не переобъясняем** здесь суть сущностей/экранов — только справочные срезы.
  Смысл экранов — в Screen Guides, сущностей — в [DOMAIN_MODEL](../DOMAIN_MODEL.md).
- **Синхронизация:** при изменении `platform-routes.md` обновляем эти файлы;
  расхождение UI↔бэкенд (напр. Freelancer = Service Provider, Storekeeper =
  warehouse) фиксируем, не нормализуем молча.
- `last_updated` отражает дату последней сверки с raw-источником.

**Синхронизировано с `platform-routes.md`:** 2026-07-02.
