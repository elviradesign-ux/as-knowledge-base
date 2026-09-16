# Release Checklist — Seller Exchange Knowledge Base

> Сводный чеклист готовности базы знаний к публикации + вопросы к техлиду по
> **DM8** (жизненный цикл партии / Shipment). Дата: 2026-07-09.
> Источник статусов — [CONTENT_ROADMAP](CONTENT_ROADMAP.md) (§5.7).

---

## 1. Статус готовности

| Статус | Кол-во | Комментарий |
|---|---|---|
| **approved** | **80 / 86** | RU-источник готов; см. gate'ы в §3 |
| blocked (DM8) | 5 | ART-005, 053, 063, 076, 077 |
| planned / needs validation | 1 | ART-024 (Voice of Customer, DM12) |

**По типам (approved):** Foundation 22 · Marketplace Academy 20 · Screen Guide 12
· Workflow Guide 8 · SEO/Pillar 7 · User Guide 11.

**По волнам:** Foundation 22/24 · Marketplace Terms ✅ 20/20 · Screen Guides 12/13
· Workflow Guides 8/10 · Pillar/SEO ✅ 7/7 · User Guide 11/12.

---

## 2. Готово к публикации (approved, RU)

Все approved-статьи прошли self-review по quality gates
([DOCUMENTATION_PRODUCTION_PIPELINE §6](DOCUMENTATION_PRODUCTION_PIPELINE.md)) и
готовы к публикации после закрытия gate'ов §3. Разделы:

- **Foundation / Core Entities** — `articles/foundations/` (см.
  [README](articles/foundations/README.md)).
- **Marketplace Terms** — `articles/academy/` (hub + 19 терминов).
- **Screen Guides** — `articles/screens/` (12; визуальные источники — mhtml).
- **Workflow Guides** — `articles/workflows/` (8 сценариев).
- **User Guide** — `articles/user-guide/` (11 инструкций).
- **Pillar / SEO** — `articles/pillar/` (7 hub-страниц).

---

## 3. Gate'ы до публикации (обязательно закрыть)

| # | Gate | Область | Кто | Статус |
|---|---|---|---|---|
| 1 | **Ревью вторым человеком** (автор ≠ ревьюер, [CONTRIBUTING](CONTRIBUTING.md)) | Все статьи | Product / Writer | ☐ не начато |
| 2 | **SEO / маркетинг-ревью** | Pillar (ART-080–086) | Marketing | ☐ не начато |
| 3 | **Скриншоты** | Screen Guides | UX | ⚠️ используется mhtml; часть — только Dark/En (My Warehouse, Support, часть Notifications) — желательны Light/иные языки |
| 4 | **Проверка ссылок** | Все | QA | ✅ автопроверка пройдена (битых нет) |
| 5 | **Экспорт в Framer CMS** | Все | Marketing / Writer | ☐ механизм не определён (см. §11 пайплайна) |
| 6 | **Владельцы (`owner`)** | Все | Product | ⚠️ везде `owner: TBD` — назначить |

---

## 4. Заблокировано до DM8 (5 статей)

Не публикуются до подтверждения жизненного цикла партии и сущности Shipment.
Шаблоны BLOCKED с причинами уже созданы:

| ART | Статья | Тип | Файл |
|---|---|---|---|
| 005 | Что такое партия | Foundation | [foundations/005-batch.md](articles/foundations/005-batch.md) |
| 053 | Создать партию | User Guide | [user-guide/053-create-batch.md](articles/user-guide/053-create-batch.md) |
| 063 | Партии — ожидающие отправки | Screen Guide | _(не создан; planned/blocked)_ |
| 076 | Клиент отправляет коробки в партию | Workflow Guide | [workflows/076-…md](articles/workflows/076-client-sends-boxes-into-batch.md) |
| 077 | Сторкипер формирует партию | Workflow Guide | [workflows/077-…md](articles/workflows/077-storekeeper-forms-batch.md) |

> Уже approved-статьи, которые лишь **ссылаются** на партию (004-box, batches-sent,
> 052-manage-boxes и др.), публиковать можно — в них lifecycle партии помечен
> *Needs validation*, а не утверждается.

---

## 5. Прочее открытое (не DM8)

- **ART-024 Voice of Customer** — `needs validation` (**DM12**): дождаться
  уточнения по Return Badge / concession_rate.
- **Локализация (Волна 6)** — EN/UA/ZH: отложена, проект RU-source. EN-черновики
  Foundation 001–004 существуют (`en-draft`); доводить после `approved`-апрува.

---

## 6. Рекомендуемый порядок релиза

1. Закрыть gate'ы §3 (ревью, владельцы, экспорт в CMS).
2. Опубликовать approved-разделы (Foundation → Marketplace Terms → Screen/Workflow
   Guides → User Guide).
3. Pillar — после SEO/маркетинг-ревью.
4. Получить ответы по **DM8** → разблокировать 5 партийных статей.
5. Получить ответ по **DM12** → ART-024.
6. Запустить локализацию (Волна 6).

---

# 7. Вопросы к техлиду — DM8 (жизненный цикл партии / Shipment)

> **Зачем:** без ответов нельзя финализировать 5 статей о партиях (§4). Сейчас в
> базе знаний по партии есть только вкладки (ожидающие / отправленные / архив) —
> **нет числовых статусов, переходов и роли Shipment**. Источник — раздел
> «Batch» в [ENTITY_STATES](ENTITY_STATES.md), [DOMAIN_MODEL §8/§11](DOMAIN_MODEL.md),
> трекер [DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md) (DM8).

### DM8.1 — Статусы партии 🔴 P0
**Контекст:** у Batch есть вкладки awaiting-send / sent-batches / archive, но нет
числовых кодов статусов, как у заказа/товара.
**Вопрос:** какие статусы у **партии** и переходы между ними (создание → запрос
на отправку → в пути → принята → архив)? Есть ли числовые коды (как `orderStatus`)?
**Разблокирует:** ART-005, 053, 076, 077 (раздел «Жизненный цикл»).

### DM8.2 — Shipment: сущность или lifecycle? 🔴 P0
**Контекст:** в модели помечено *Needs validation* — Shipment это отдельная
сущность или жизненный цикл коробки. Есть статусы на складе: `NEW` (в пути на преп
Китая) → `ACCEPTED_IN_PROCESSING` → `IN_STOCK` → `REQUESTED_SEND_TO_BATCH` →
`IN_BATCH` → `IN_BATCH_ON_THE_WAY` → `FINISH_PREP_CENTR_USA`.
**Вопрос:** «Shipment» — это отдельная сущность или именно этот жизненный цикл
коробки/партии? Если сущность — какие у неё поля и как связана с Batch и Box?
**Разблокирует:** трактовку связей Box/Batch → Shipment (ER #41, #43).

### DM8.3 — Prep ID в цепочке 🟡 P1
**Контекст:** есть модалка `GeneratePrepIdModal` (генерация Prep ID) и поле Prep ID
у партии.
**Вопрос:** на каком шаге генерируется Prep ID и обязателен ли он для отправки
партии? Кто его генерирует?
**Разблокирует:** шаги в ART-077 (формирование партии).

### DM8.4 — Границы ролей: клиент vs сторкипер 🟡 P1
**Контекст:** есть два сценария — WF-035 «Клиент отправляет коробки в партию» и
WF-041 «Сторкипер формирует партию».
**Вопрос:** кто и что именно делает при формировании/отправке партии — где
граница между клиентом (запрос на отправку) и сторкипером (сборка/отправка)?
**Разблокирует:** ART-076 vs ART-077 (разделение шагов).

### DM8.5 — Что именно разблокирует каждую статью 🟢 P2
**Вопрос (сводный):** после ответов DM8.1–DM8.4 — достаточно ли этого, чтобы
финализировать все 5 статей (§4), или есть ещё зависимости (напр. отдельные
статусы «архива», отмена партии)?

---

## Как вносить ответы

Ответы DM8 → правим [ENTITY_STATES](ENTITY_STATES.md) (добавляем статусы партии),
[DOMAIN_MODEL](DOMAIN_MODEL.md) (§8 lifecycle, §11 — снимаем NV по Shipment),
[ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md) (#41, #43), затем заполняем 5
BLOCKED-шаблонов и переводим их в `review`/`approved`. Трекер —
[DOMAIN_MODEL_OPEN_QUESTIONS](DOMAIN_MODEL_OPEN_QUESTIONS.md).
