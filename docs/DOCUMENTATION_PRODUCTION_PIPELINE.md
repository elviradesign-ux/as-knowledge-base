# Documentation Production Pipeline

> Операционный хендбук производства документации Seller Exchange (внутр.
> **AmazonService / AS**): как статьи создаются, проверяются, публикуются и
> поддерживаются. Рабочий язык — **RU-first** ([LOCALIZATION_GUIDE](LOCALIZATION_GUIDE.md)).
>
> Документ **не дублирует** содержимое источников — он описывает **процесс** и
> ссылается на них: философию см. в [MANIFESTO](MANIFESTO.md), правила текста —
> [STYLE_GUIDE](STYLE_GUIDE.md), процесс правок — [CONTRIBUTING](CONTRIBUTING.md),
> план — [CONTENT_ROADMAP](CONTENT_ROADMAP.md).

---

## 1. Назначение

Документ описывает полный жизненный цикл документации и превращает её создание в
**повторяемый производственный процесс**. Пайплайн гарантирует:

- **согласованность** — единый шаблон, стиль и терминология;
- **фактическую точность** — источник правды выше статьи, «точность > полноты»;
- **масштабируемость** — новые статьи выпускаются по одному конвейеру;
- **готовность к локализации** — RU-источник → EN/UA/ZH;
- **совместимость с CMS** — front matter → Framer;
- **совместимость с AI** — структурированные метаданные и явные источники.

## 2. Источник правды (иерархия)

Информация всегда течёт **вниз**, никогда — вверх. Статья **не переопределяет**
доменную модель и справочники.

```
DOMAIN_MODEL.md              (сущности, домены)
        ↓
ENTITY_RELATIONSHIPS.md      (связи, кардинальность)
        ↓
GLOSSARY.md                  (термины, поля Инвентаря)
        ↓
SCREEN_CATALOG.md            (экраны SCR-###)
        ↓
WORKFLOW_CATALOG.md          (сценарии WF-###)
        ↓
CONTENT_ROADMAP.md           (план статей ART-###)
        ↓
articles/                    (статьи: RU-источник + переводы)
        ↓
Framer CMS                   (коллекции, поля)
        ↓
Published Knowledge Base     (seller.exchange / Academy)
```

**Правило:** если статья противоречит источнику — правится статья, а не источник.
Изменение факта вносится сначала в верхний уровень (Domain Model / Glossary /
Entity States), затем в зависимые статьи (см. [CONTRIBUTING](CONTRIBUTING.md)).
Статусы сущностей — только в [ENTITY_STATES](ENTITY_STATES.md).

## 3. Типы документации

Типы согласованы с [CONTENT_ROADMAP §3](CONTENT_ROADMAP.md) и
[INFORMATION_ARCHITECTURE](INFORMATION_ARCHITECTURE.md).

| Тип | Назначение | Аудитория | Источники | Результат | Зависит от |
|---|---|---|---|---|---|
| **Foundation** | «Что такое X» — ключевая сущность | Новые продавцы, команда | DOMAIN_MODEL, ENTITY_RELATIONSHIPS, GLOSSARY | Концепт-статья (`articles/foundations/`) | — |
| **Glossary** | Определение термина | Все | Реальные данные, локализации | Запись в [GLOSSARY](GLOSSARY.md) | — |
| **Marketplace Academy** | Обучение работе на Amazon | Продавцы | Foundation + Glossary + отраслевые знания | Учебная статья | Foundation, Glossary |
| **Screen Guide** | Справочник по экрану/модалке | Пользователи | SCREEN_CATALOG + текущий UI + UX-ревью | Гайд (`articles/screens/`) | стабильный экран |
| **Workflow Guide** | Сквозной сценарий по ролям | Пользователи | WORKFLOW_CATALOG + Foundation + Screen Guide | Пошаговый гайд | Foundation, Screen Guide |
| **User Guide** | Как выполнить задачу в продукте | Пользователи | Foundation + Screen Guide + Workflow | Инструкция | Foundation |
| **FAQ** | Частые вопросы | Все | Support-тикеты, статьи | Список Q&A | базовые статьи |
| **Troubleshooting** | Проблема → причина → решение | Пользователи, поддержка | ENTITY_STATES, Screen/Workflow Guide | Диагностическая статья | Workflow Guide |
| **Release Notes** | Хроника изменений | Все | Патч-ноуты продукта | Запись релиза | — |
| **Internal Reference** | Внутренний документ команды | Команда | Любые источники | Внутренняя страница | — |
| **SEO / Pillar** | Органический трафик, связка Academy↔продукт | Внешняя аудитория | Academy + Foundation + позиционирование | Крупная статья | Glossary, Academy |

## 4. Производственный пайплайн статьи

13 стадий. Ответственные помечены по ролям (§14); там, где владелец не закреплён
в КБ (везде `owner: TBD`) — **Needs validation**.

| # | Стадия | Назначение | Входы | Выходы | Ответственный | Критерий выхода |
|---|---|---|---|---|---|---|
| 1 | **Idea** | Зафиксировать потребность в статье | Пробел в покрытии, запрос | Заявка на статью | Technical Writer / Product | Тема сформулирована как задача читателя |
| 2 | **Roadmap** | Внести в план, присвоить `ART-###` | Заявка | Строка в [CONTENT_ROADMAP](CONTENT_ROADMAP.md) | Technical Writer | Есть ID, тип, source entity, статус `planned` |
| 3 | **Template** | Создать каркас по шаблону | ARTICLE_TEMPLATE | Файл со `status: template` | Technical Writer | Front matter заполнен, плейсхолдеры и source notes |
| 4 | **Draft** | Написать RU-текст | Источники §5, шаблон | `status: draft` (ru) | Technical Writer | Все секции заполнены, ссылки вместо дублей |
| 5 | **Fact Validation** | Сверить факты с источником правды | DOMAIN_MODEL, ENTITY_STATES, GLOSSARY | Отмеченные факты / `needs validation` | Product / Backend | Нет непроверенных утверждений; спорное помечено |
| 6 | **Technical Review** | Проверка технической корректности | Draft + бэкенд-факты | Замечания устранены | Backend / Product | Термины, статусы, права верны |
| 7 | **UX Review** | Проверка UI и скриншотов | Draft + текущий UI | Актуальные скриншоты | UX | UI соответствует, скриншоты без ПДн |
| 8 | **Editorial Review** | Стиль, ясность, единый тон | Draft + [STYLE_GUIDE](STYLE_GUIDE.md) | Отредактированный текст | Technical Writer (не автор) | Стиль-гайд соблюдён |
| 9 | **Approval** | Финальное утверждение RU | Отревьюенный текст | `status: approved` | Product / Owner | Ревьюер ≠ автор ([CONTRIBUTING](CONTRIBUTING.md)) |
| 10 | **Localization** | Переводы из утверждённого RU | RU `approved` | EN/UA/ZH переводы | Localization | Термины из GLOSSARY, форматы по гайду |
| 11 | **CMS Import** | Загрузка в Framer | Markdown + front matter | Запись в коллекции | Marketing / Writer | Поля смэплены (§9), связи проставлены |
| 12 | **Publication** | Публикация | Запись CMS | `status: published` | Marketing | Страница доступна, ссылки рабочие |
| 13 | **Maintenance** | Поддержка актуальности | `review_by`, изменения продукта | Обновлённая статья | Owner | Дата ревизии продлена/статья обновлена |

## 5. Правила генерации статей

Каждый тип собирается из фиксированных источников. Статья **никогда не становится
самостоятельным источником правды**.

| Тип | Собирается из |
|---|---|
| **Foundation** | DOMAIN_MODEL + ENTITY_RELATIONSHIPS + GLOSSARY |
| **Marketplace Academy** | Foundation + GLOSSARY + отраслевые знания (помечать внешние факты) |
| **Screen Guide** | SCREEN_CATALOG + текущий UI + UX-ревью |
| **Workflow Guide** | WORKFLOW_CATALOG + Foundation + Screen Guide |
| **SEO / Pillar** | Academy + Foundation + продуктовое позиционирование |
| **FAQ / Troubleshooting** | Support-тикеты + ENTITY_STATES + существующие статьи |

Пример уже реализован: [articles/foundations/001-product.md](articles/foundations/001-product.md)
(Foundation) ссылается на GLOSSARY/ENTITY_STATES/ENTITY_RELATIONSHIPS, а
[articles/screens/inventory-products.md](articles/screens/inventory-products.md)
(Screen Guide) — на SCREEN_CATALOG и локализации.

## 6. Quality Gates (обязательные проверки)

Статья не переходит в `approved`, пока не пройдёт все ворота (расширяет чеклист
из [STYLE_GUIDE](STYLE_GUIDE.md)):

| # | Ворота | Что проверяем |
|---|---|---|
| 1 | **Terminology** | Термины и имена ролей — как в GLOSSARY / PERMISSIONS_MATRIX; статусы дословно из ENTITY_STATES |
| 2 | **Links** | Внутренние ссылки рабочие, относительные пути верны |
| 3 | **Screenshots** | Актуальны, без реальных ПДн, единый хром |
| 4 | **Metadata** | Front matter полон (тип, статус, entities, roles, source_documents) |
| 5 | **Workflow references** | `WF-###` существуют в WORKFLOW_CATALOG |
| 6 | **Glossary references** | Термины ведут в GLOSSARY, не переопределяются в тексте |
| 7 | **Related entities** | Указаны и соответствуют DOMAIN_MODEL |
| 8 | **Localization** | Пригодность к переводу; RU — источник |
| 9 | **SEO** | `seo_title` / `seo_description` заполнены (для публичных типов) |
| 10 | **Factual validation** | Нет непроверенных утверждений; спорное помечено `needs validation` |

## 7. Правила валидации

Наследуют философию [DOMAIN_MODEL §11](DOMAIN_MODEL.md) и
[DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md):

- **Точность важнее полноты.**
- **Не выдумывать**: сущности, связи, статусы, бизнес-правила, права, термины.
- При неопределённости — пометка **Needs validation** и вынос в **Open Question**
  (в статье и/или в трекере открытых вопросов).
- Расхождения UI↔бэкенд документируются **оба** (например, Freelancer =
  Service Provider), не нормализуются молча.
- Не финализировать статьи, зависящие от нерешённого (напр. **Batch/Shipment —
  DM8**, см. [CONTENT_ROADMAP §7](CONTENT_ROADMAP.md)).

## 8. Автоматическое связывание

Каждая статья автоматически ссылается на:

| Связь | Источник генерации |
|---|---|
| Related entities | DOMAIN_MODEL §4 (карточки сущностей) |
| Related articles | CONTENT_ROADMAP (`ART-###`) + `related_articles` во front matter |
| Related screens | SCREEN_CATALOG (`SCR-###`) |
| Related workflows | WORKFLOW_CATALOG (`WF-###`) |
| Related glossary terms | GLOSSARY (первое упоминание термина) |
| Related modules | INFORMATION_ARCHITECTURE §6 (карта модулей) |
| Related roles | PERMISSIONS_MATRIX |

**Как генерируются:** для сущности-источника статьи берём её строки из
[ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md) (Source/Target) → получаем список
связанных сущностей → по CONTENT_ROADMAP находим соответствующие `ART-###` →
проставляем в `related_*`. Экраны/сценарии — из карточки сущности в DOMAIN_MODEL.
На текущем этапе связывание **ручное по этим правилам**; автоматизация — §16.

## 9. Конвейер Framer CMS

```
Markdown (RU-источник + переводы)
        ↓
Front Matter (метаданные)
        ↓
CMS Collections (Articles / Entities / Tags)
        ↓
Related Articles (связи ART-###)
        ↓
Published Pages
```

Маппинг полей — см. [CONTENT_ROADMAP §8](CONTENT_ROADMAP.md). Синхронизируются
автоматически: `title`, `slug`, `article_type`, `section`, `status`, `locale`,
`roles`, `modules`, `entities`, `workflows`, `screens`, `related_articles`,
`seo_title`, `seo_description`. Служебные (`owner`, `review_by`,
`validation_status`) — для внутреннего контроля, публикацией не выводятся.
**Needs validation:** формат экспорта Markdown→Framer (плагин/скрипт/ручной) не
определён.

## 10. Конвейер локализации

RU-first ([LOCALIZATION_GUIDE](LOCALIZATION_GUIDE.md)):

```
RU Draft → RU Review → RU Approved
        ↓
EN Translation → UA Translation → ZH Translation
        ↓
Localization QA
        ↓
Published (по локали)
```

- Переводы создаются **только из утверждённого RU** (`approved`).
- Файлы: `00X.md` = RU-источник, `00X.<lang>.md` = перевод (`translation_of`).
- Переводы **никогда не становятся источником**; RU — канон. Правка факта — в
  RU-источнике, затем ре-синхронизация переводов (их статус → `review`).
- Порядок языков в продукте: EN / RU / ZH / UA; термины UI — из «Динамических
  переводов» продукта, не на слух.

> Текущее состояние: EN-черновики Foundation 001–004 существуют как
> предварительные переводы (`en-draft`); доводятся до `en-ready` после `approved`
> RU.

## 11. Генерация статей с помощью AI

AI-ассистент **всегда стартует от источников**, а не от предположений:

- Обязательные входы: DOMAIN_MODEL, ENTITY_RELATIONSHIPS, CONTENT_ROADMAP,
  GLOSSARY, WORKFLOW_CATALOG, SCREEN_CATALOG.
- **Не выдумывать факты.** Неизвестное → `needs validation` + Open Question.
- Каждая сгенерированная статья обязана содержать: `source_documents`,
  явные `related entities`, пометки `needs validation` там, где источник не
  подтверждает.
- Соблюдать RU-first: генерировать RU-источник; переводы — отдельная стадия.
- Соблюдать «один факт — одно место»: ссылаться, не переписывать справочники.

## 12. Knowledge Graph

Одна сущность — много представлений, **без дублирования фактов**:

```
Entity (DOMAIN_MODEL)
        ↓
Foundation  → Screen Guide → Workflow Guide → Academy → FAQ → SEO
```

Каждый узел ссылается на одну и ту же сущность и её связи из
[ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md); факты живут в источнике, статьи
дают разные «проекции» под аудиторию и задачу. Так roadmap + связи образуют граф
знаний, пригодный для навигации, поиска и AI-эмбеддингов.

## 13. Поддержка контента

Изменение продукта запускает каскад ревизий сверху вниз:

```
UI update → Screen Guide review → Workflow review → Foundation review
          → Academy review → SEO review
```

| Триггер | Что пересматриваем | Частота |
|---|---|---|
| Изменение UI экрана | Screen Guide → зависимые Workflow | по факту релиза |
| Изменение статусов/связей | ENTITY_STATES/RELATIONSHIPS → Foundation → всё зависимое | по факту |
| Плановая ревизия | Любая статья по `review_by` | каждые ~3 мес (поле `review_by`) |
| Патч-ноут | Release Notes | по релизу |

Владелец (`owner`) следит за `review_by` и продлевает/обновляет
([CONTRIBUTING](CONTRIBUTING.md)). **Needs validation:** точная периодичность —
на согласование (см. §17).

## 14. Роли и ответственность

Матрица. Поскольку в КБ владельцы не закреплены (`owner: TBD`), назначение
ответственных — **Needs validation**.

| Роль | Ответственность в пайплайне |
|---|---|
| **UX** | UX-ревью (стадия 7), актуальность скриншотов, соответствие UI |
| **Product** | Fact validation, приоритеты roadmap, финальный approval |
| **Backend** | Подтверждение сущностей/статусов/прав; ответы на DM-вопросы |
| **QA** | Проверка ссылок, метаданных, quality gates |
| **Technical Writer** | Draft, editorial review, ведение roadmap и шаблонов |
| **Marketing** | SEO, CMS import, публикация, Pillar-статьи |
| **Support** | Поставка тем для FAQ/Troubleshooting из тикетов |
| **Localization** | Переводы из approved RU, локализационный QA |
| **AI** | Генерация черновиков от источников, автосвязывание, эмбеддинги |

## 15. KPI документации

| Метрика | Что измеряет |
|---|---|
| Coverage | Доля сущностей/экранов/сценариев с покрытием статьями |
| Articles Published | Число опубликованных статей |
| Broken Links | Количество битых внутренних/внешних ссылок |
| Localization Progress | Доля `approved` RU, переведённых на EN/UA/ZH |
| Validation Issues | Число открытых `needs validation` / Open Questions |
| Average Review Time | Среднее время прохождения ревью (стадии 5–9) |
| Content Freshness | Доля статей с непросроченным `review_by` |
| SEO Traffic | Органический трафик на Pillar/Academy |
| Academy Completion | Прохождение обучающих материалов |
| Workflow Coverage | Доля `WF-###` с готовым Workflow Guide |

## 16. Будущая автоматизация

| Возможность | Идея |
|---|---|
| Draft из Domain Model | Генерировать каркас Foundation-статьи по карточке сущности |
| FAQ из Support-тикетов | Собирать частые вопросы из обращений |
| Screen Guide из UI-метаданных | Тянуть элементы/действия из метаданных экрана |
| Авто-Related Articles | Проставлять связанные `ART-###` по графу |
| Авто-внутренние ссылки | Автолинковать термины/сущности при первом упоминании |
| Локализационные пакеты | Формировать наборы строк на перевод из approved RU |
| Генерация Release Notes | Собирать патч-ноуты из изменений |
| CMS-импорт | Автоэкспорт Markdown→Framer с маппингом полей |
| AI-эмбеддинги | Индексация статей и графа для поиска/ассистента |

## 17. Открытые вопросы

- Кто владелец каждой роли из §14 (сейчас `owner: TBD`)? — **Needs validation**.
- Периодичность плановых ревизий (`review_by`) и публикаций (cadence)?
- Механизм экспорта Markdown → Framer CMS (плагин / скрипт / ручной)?
- Academy: остаётся RU-first внутренне, но публикуется EN-first? (см.
  [CONTENT_ROADMAP §9](CONTENT_ROADMAP.md)).
- Какие статьи публичные, какие — Internal Reference?
- Кто финально отвечает за product accuracy и за локализацию?
- Инструмент проверки битых ссылок и метаданных в CI?
- Batch/Shipment-статьи заблокированы до **DM8** — срок ответа?

> Открытые вопросы по сущностям/связям — в
> [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md).
