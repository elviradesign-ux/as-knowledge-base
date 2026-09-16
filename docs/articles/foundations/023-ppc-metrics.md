---
title: "Что такое PPC-метрики"
slug: ppc-metrics
article_type: Foundation
series: "Foundations / Core Entities"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client]
modules: [Advertising, Analytics]
entities: [PPC Metrics, Campaign, Product]
workflows: []
related_screens: [SCR-120, SCR-122]
related_entities: [Campaign, Product, Report]
related_articles: [022-campaign, 001-product]
seo_title: "PPC-метрики в Seller Exchange — показатели платной рекламы"
seo_description: "Что такое PPC-метрики в Seller Exchange: показатели платной рекламы Amazon — показы, клики, CPC, CTR, рекламные продажи, TACoS и ACoS."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - DOMAIN_MODEL.md (§4 PPC Metrics / Campaign)
  - GLOSSARY.md (поля рекламы Инвентаря)
  - ENTITY_RELATIONSHIPS.md (#86)
  - SCREEN_CATALOG.md (SCR-120, SCR-122)
validation_status: confirmed
---

> **Канонический источник (ru).** Переводы создаются из этого файла после
> отдельного решения. При правках сначала меняем источник.

# Что такое PPC-метрики

**PPC-метрики** — показатели платной рекламы Amazon (Pay-Per-Click) по товару.
Они измеряют, как работает [кампания](022-campaign.md): сколько показов, кликов,
продаж и во сколько это обошлось.

## Кратко

PPC-метрики показывают эффективность рекламы: показы и клики, стоимость клика,
рекламные продажи и доля затрат на рекламу. Метрики считаются по товару и видны
в инвентаре и отчётах.

## Что это такое

PPC-метрики — производные показатели над данными рекламы. Полные определения полей
хранятся в справочнике инвентаря и здесь не дублируются — см.
[GLOSSARY → поля рекламы](../../GLOSSARY.md).

## Основные показатели

- **Показы (Adv Impressions)** и **Клики (Adv Clicks)**.
- **CPC (Adv Cpc)** — средняя цена за клик; **CTR (Adv Ctr)** — доля кликов от показов.
- **Рекламные продажи (Adv Sales)** и **заказы (Adv Orders)**.
- **Конверсия (Adv Conversion Percentage)** — доля кликов, приведших к заказу.
- **TACoS** — доля всей выручки, уходящая на рекламу.
- **ACoS** — отношение рекламных затрат к продажам от рекламы.

> Подробный разбор ACoS / TACoS / ROAS — отдельная статья _(планируется, ART-042)_.

## Зачем это нужно

- Показывают, окупается ли реклама.
- Помогают управлять ставками и бюджетом.
- Разделяют органические и рекламные продажи.

## Жизненный цикл и статусы

Отдельного набора статус-кодов у PPC-метрик нет — это производные показатели.

## Связи с другими сущностями

- PPC-метрики относятся к **кампании** и **товару**.
- Данные входят в **отчёты** по рекламе (PPC_*, CAMPAIGNS).

Точные связи — в [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## Кто работает с этой сущностью

С рекламной аналитикой работает **Client** — по своим товарам. Доступ — см.
[Permissions Matrix](../../PERMISSIONS_MATRIX.md).

## Где это видно в интерфейсе

| Экран | Что вы там делаете |
|---|---|
| [SCR-120](../../SCREEN_CATALOG.md) Инвентарь — товары | Рекламные метрики по товару |
| [SCR-122](../../SCREEN_CATALOG.md) Инвентарь — отчёты | Отчёты по рекламе |

## Связанные сценарии

Отдельного сценария в каталоге нет — метрики сопровождают рекламную аналитику.

## Термины и справочники

- Поля рекламы: [GLOSSARY](../../GLOSSARY.md) (раздел «Реклама»).
- Связи: [Entity Relationships](../../ENTITY_RELATIONSHIPS.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Чем ACoS отличается от TACoS? | ACoS — затраты к продажам от рекламы; TACoS — доля всей выручки на рекламу. Подробнее — ART-042. |
| Где взять все определения полей? | В справочнике полей инвентаря ([GLOSSARY](../../GLOSSARY.md)). |
| Метрики считаются по кампании или по товару? | Отражены по товару; связаны с кампаниями. |

## Связанные статьи

- [022 — Кампания](022-campaign.md)
- [001 — Товар](001-product.md)
- ACoS / TACoS / ROAS — планируется (ART-042)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] Related entities — соответствуют [DOMAIN_MODEL](../../DOMAIN_MODEL.md).
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования — определения полей даны ссылкой на GLOSSARY.
- [x] Глубокий разбор ACoS/TACoS/ROAS вынесен в ART-042 (планируется).
- [x] Внутренние ссылки корректны.
