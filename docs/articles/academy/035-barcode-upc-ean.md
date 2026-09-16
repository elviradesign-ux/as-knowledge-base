---
title: "Баркод / UPC / EAN"
slug: barcode-upc-ean
article_type: Marketplace Academy
series: "Marketplace Terms"
section: Marketplace Academy
status: approved
difficulty: beginner
locale: ru
localization_status: ru-source
audience: [Новые продавцы, Команда платформы]
roles: [Client, Storekeeper, Buyer, Admin]
modules: [Product, Inventory, Warehouse]
entities: [Barcode, FNSKU, Product]
workflows: []
related_screens: [SCR-120]
related_entities: [Product, FNSKU, ASIN]
related_articles: [026-asin, 028-asin-vs-sku-vs-fnsku, 025-marketplace-terms]
seo_title: "Баркод / UPC / EAN — штрихкоды товара"
seo_description: "Что такое баркод, UPC и EAN: штрихкоды товара, чем они отличаются и как связаны с FNSKU в Seller Exchange."
owner: TBD
last_updated: 2026-07-02
review_by: 2026-10-02
locales: [en, ru, zh, ua]
source_documents:
  - GLOSSARY.md (Баркод)
  - DOMAIN_MODEL.md (§4 Barcode; UPC/EAN — атрибуты, DM13)
  - SCREEN_CATALOG.md (SCR-120)
validation_status: confirmed
---

> **Канонический источник (ru).** Статья серии Marketplace Terms. Переводы
> создаются из этого файла после отдельного решения.

# Баркод / UPC / EAN

**Баркод** (штрихкод) — код на упаковке товара, по которому его идентифицируют и
принимают на складе. **UPC** и **EAN** — это форматы штрихкода (атрибуты баркода),
а не отдельные сущности (подтверждено, DM13).

## Кратко

Баркод — «этикетка» товара для сканирования. UPC и EAN — распространённые
международные форматы штрихкодов. На складах FBA роль штрихкода может выполнять
**FNSKU**.

## Что это такое

- **Баркод** — штрихкод товара в целом.
- **UPC** (Universal Product Code) — формат штрихкода (атрибут).
- **EAN** (International Article Number) — формат штрихкода (атрибут).
- **FNSKU** — внутренний код Amazon для склада FBA (см.
  [ASIN vs SKU vs FNSKU](028-asin-vs-sku-vs-fnsku.md)).

## Зачем это нужно

- Баркод нужен для идентификации и приёмки товара на складе.
- Правильный штрихкод ускоряет складские операции.
- Понимание UPC/EAN/FNSKU снижает путаницу при маркировке.

## Где это видно в интерфейсе

Баркод отражён полем товара в
[инвентаре](../foundations/002-inventory.md)
([SCR-120](../../SCREEN_CATALOG.md)); работа со штрихкодом и HS-кодом — модалка
`BarHsCodeModal`.

## Термины и справочники

- Идентификаторы: [ASIN vs SKU vs FNSKU](028-asin-vs-sku-vs-fnsku.md).
- Термин: [Баркод](../../GLOSSARY.md).

## FAQ

| Вопрос | Ответ |
|---|---|
| UPC и EAN — отдельные сущности? | Нет, это форматы (атрибуты) баркода (DM13). |
| Чем баркод отличается от FNSKU? | FNSKU — код Amazon для склада FBA; на FBA он может выступать штрихкодом товара. |
| Где работать со штрихкодом? | В инвентаре и модалке штрих-кода/HS-кода (`BarHsCodeModal`). |

## Связанные статьи

- [Что такое ASIN](026-asin.md)
- [ASIN vs SKU vs FNSKU](028-asin-vs-sku-vs-fnsku.md)
- [Термины маркетплейса](025-marketplace-terms.md)

## Чеклист ревью

- [x] Терминология — по [GLOSSARY](../../GLOSSARY.md).
- [x] Метаданные — front matter полон (`article_type: Marketplace Academy`, `series: Marketplace Terms`).
- [x] UPC/EAN описаны как атрибуты баркода (DM13), не выдуманы как сущности.
- [x] Source documents — перечислены и актуальны.
- [x] Нет дублирования — идентификаторы даны ссылкой на ART-028.
- [x] Внутренние ссылки корректны (academy↔foundations).
