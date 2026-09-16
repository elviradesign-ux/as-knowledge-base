---
title: "ACoS / TACoS / ROAS"
slug: acos-tacos-roas
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Admin]
modules: [Advertising, Analytics]
entities: [PPC Metrics, Campaign, Product]
workflows: []
related_screens: [SCR-120, SCR-122]
related_entities: [Campaign, Product, Report]
related_articles: [023-ppc-metrics, 022-campaign, 025-marketplace-terms]
seo_title: "ACoS, TACoS и ROAS — метрики эффективности рекламы Amazon"
seo_description: "Что такое ACoS, TACoS и ROAS: ключевые метрики эффективности рекламы Amazon, чем они различаются и как их читать в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (Acos Percentage, Tacos, Adv Sales, Adv Cost)
  - DOMAIN_MODEL.md (§4 PPC Metrics)
  - SCREEN_CATALOG.md (SCR-120, SCR-122)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# ACoS / TACoS / ROAS

Три метрики оценивают эффективность рекламы Amazon. **ACoS** и **TACoS**
присутствуют как поля в инвентаре Seller Exchange; **ROAS** — распространённая
отраслевая метрика, обратная ACoS.

## Кратко

- **ACoS** — какая доля продаж **от рекламы** ушла на рекламу.
- **TACoS** — какая доля **всей** выручки ушла на рекламу.
- **ROAS** — сколько выручки принёс каждый рубль/доллар рекламы (отраслевой термин).

## Определения

- **ACoS** (Advertising Cost of Sales) — отношение рекламных затрат к продажам,
  полученным от рекламы. Ниже — эффективнее. Поле `Acos Percentage`.
- **TACoS** (Total Advertising Cost of Sales) — доля рекламных затрат в **общей**
  выручке (органика + реклама). Показывает влияние рекламы на весь бизнес.
  Поле `Tacos`.
- **ROAS** (Return on Ad Spend) — выручка от рекламы на единицу рекламных затрат;
  по смыслу обратна ACoS. Это стандартная отраслевая метрика.

## Как читать

- Низкий **ACoS** — реклама окупается на уровне рекламных продаж.
- Снижение **TACoS** со временем — бизнес меньше зависит от платной рекламы.
- Высокий **ROAS** — больше выручки на каждый вложенный в рекламу рубль/доллар.

Полные определения полей — в [PPC-метрики](../foundations/023-ppc-metrics.md) и
[справочнике полей](../../GLOSSARY.md).

## Где это видно в интерфейсе

ACoS и TACoS — поля рекламы в [инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)); сводно — в отчётах
([SCR-122](../../SCREEN_CATALOG.md)).

## Термины и справочники

- Общий обзор: [PPC-метрики](../foundations/023-ppc-metrics.md).
- Кампании: [Что такое кампания](../foundations/022-campaign.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| Чем ACoS отличается от TACoS? | ACoS — доля затрат в продажах **от рекламы**; TACoS — доля затрат в **общей** выручке. |
| ROAS есть как поле в системе? | ACoS/TACoS — поля инвентаря; ROAS — отраслевая метрика (обратная ACoS). |
| Что лучше — низкий ACoS или высокий ROAS? | Это связанные показатели: низкий ACoS ≈ высокий ROAS. |

## Связанные статьи

- [023 — PPC-метрики](../foundations/023-ppc-metrics.md)
- [022 — Кампания](../foundations/022-campaign.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон.
- [x] ACoS/TACoS — поля платформы; ROAS помечен как отраслевая метрика, не выдуман как поле.
- [x] Source documents — перечислены и актуальны.
- [x] Внутренние ссылки корректны (academy↔foundations).
