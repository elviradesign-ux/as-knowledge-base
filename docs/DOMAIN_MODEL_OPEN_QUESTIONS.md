# Domain Model — открытые вопросы для tech lead / product

> **Цель:** закрыть пункты **Needs validation** из [DOMAIN_MODEL](DOMAIN_MODEL.md) §11
> и связи `?` из [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md), чтобы доменная
> модель Seller Exchange стала фактически верной (сейчас 15 связей — Needs
> validation, 50 — с неизвестной кардинальностью).
> **Когда задавать:** sync с tech lead / product. Ответы вносим в
> [DOMAIN_MODEL](DOMAIN_MODEL.md), [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md),
> [GLOSSARY](GLOSSARY.md), [ENTITY_STATES](ENTITY_STATES.md).
> **Источники:** [DOMAIN_MODEL](DOMAIN_MODEL.md), [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md),
> [ENTITY_STATES](ENTITY_STATES.md), raw `platform-routes.md`,
> `figma-mcp/docs/Data filters*.md`.
> **Формат:** каждый вопрос → Контекст · Вопрос · Что блокирует. В скобках —
> ссылка на пункт DOMAIN_MODEL §11 и/или строки таблицы ENTITY_RELATIONSHIPS.
>
## Ответы (2026-07-01)

Закрыто 15/19. Ответы внесены в [DOMAIN_MODEL](DOMAIN_MODEL.md) §4/§11,
[ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md), [ENTITY_STATES](ENTITY_STATES.md).

| # | Статус | Ответ |
|---|---|---|
| DM1 | ✅ | Order Item — связка сущностей, принадлежащая Заказу |
| DM2 | ✅ | Inventory Item = Product (карточка товара пользователя); статусы VACANT…UNLINKED = связка с Supplier Card |
| DM3 | ✅ | Account = учётка пользователя; Client = только роль; User = platform-user (любая роль); Sub-user = член команды у любой роли |
| DM4 | ✅ (частично) | Research Product = Product в статусах 0–15/200–205; связь с Idea уточняется |
| DM5 | ✅ | Listing — набор отчётов |
| DM6 | ⏳ | Connected App / Apps Marketplace — функционал в разработке |
| DM7 | ✅ | Supplier Search Request — мульти-ролевой: Client сам или через Buyer |
| DM8 | ⏳ | Batch lifecycle — ответ позже |
| DM9 | ✅ | Support Ticket = запрос пользователя; Feedback = ответ Админа/модератора |
| DM10 | ✅ | Permission Preset — без lifecycle, просто набор |
| DM11 | ✅ | Milestone — глобальная; крепится к Service Request и к Idea |
| DM12 | ✅ | Voice of Customer — срез: concession_rate, badge_status; Return Badge в NCX rating |
| DM13 | ✅ | SKU / UPC / EAN — атрибуты |
| DM14 | ✅ | Super Box существует — контейнер из коробок (SB) |
| DM15 | ❓ | Dashboard Widget — без ответа |
| DM16 | ✅ | Announcement — карточка Услуги (объявление Service Provider) |
| DM17 | ✅ | Brand Launch — процесс (неск. Product Launch = Brand Launch); флоу/описания пока нет |
| DM18 | ✅ | Variation = Product; Parent = связь/зависимость |
| DM19 | ⏳ | Определения отчётов — уточняется |

Легенда: ✅ закрыто · ⏳ ответ позже · ❓ без ответа.

---

## A. К tech lead / backend — существование сущностей 🔴 P0

> Без ответов каталог сущностей содержит недоказанные объекты. Определяет, что
> вообще является сущностью, а что — атрибутом / статусом / отчётом.

### DM1. Order Item — сущность или атрибуты заказа? 🔴 P0 (§11.5; ER #15,#29)
**Контекст:** заказ содержит товары и «коробки к заказу», но отдельной сущности
`Order Item` в документации нет. Таблица `orders` — 22 колонки.
**Вопрос:** позиция заказа — самостоятельная сущность (товар + кол-во + цена в
рамках заказа), или заказ хранит товары иначе (через Box / прямую связь
product↔order)?
**Блокирует:** Entity Catalog (Order Item); связи Order↔Product (#15, #29).

### DM2. Inventory Item — товарная позиция или статус связи? 🔴 P0 (§11.6; ER #71)
**Контекст:** [ENTITY_STATES](ENTITY_STATES.md) «Статусы позиции инвентаря»
(VACANT / RESERVED / WAITING_INVITE / INVITED / REGISTERED / IN_USE / UNLINKED,
с цветами). По значениям похоже на статус связи ASIN/места с пользователем, а не
на позицию склада.
**Вопрос:** к чему относится этот enum — к товарной позиции инвентаря, к
слоту/месту ASIN или к приглашению пользователя? Как называется сущность на бэке?
**Блокирует:** Entity Catalog (Inventory Item); связь Product↔Inventory Item (#71).

### DM3. Account vs User vs Client — как разграничены? 🔴 P0 (§11.11; ER #62–65)
**Контекст:** в [GLOSSARY](GLOSSARY.md) Client и Account описаны как одно; в
роутах есть `users`, `sub-users`, `platform-users`.
**Вопрос:** Account (владелец-контрагент), User (учётка с ролью) и Client
(роль, CODE=10) — три разных объекта или проекции одного? Кто владеет
магазинами/товарами — Account или User?
**Блокирует:** домен Organization; связи владения Store/Product/Order (#62–65).

### DM4. Research Product — сущность или статус Product Card? 🔴 P0 (§11.12)
**Контекст:** в обзоре платформы «Research Products» = «product cards in
research status», видимы Researcher и Buyer.
**Вопрос:** это отдельная сущность или Product Card в диапазоне статусов
(0–15 / 200–205)? Есть ли отдельная таблица?
**Блокирует:** Entity Catalog (Research Product); домен Product Research.

### DM5. Listing — сущность или только отчёты? 🔴 P0 (§11.7; ER #72)
**Контекст:** есть `productListingReports` и экран отчётов по листингам (SCR-122),
но отдельной сущности листинга нет.
**Вопрос:** «листинг» моделируется как самостоятельная сущность (1 ASIN = 1
листинг на маркетплейсе) или это только набор отчётов над Product?
**Блокирует:** Entity Catalog (Listing); связь Listing↔Product (#72).

### DM6. Connected App / Apps Marketplace — существует ли? 🔴 P0 (§11.10)
**Контекст:** промпт доменной модели упоминал «Apps Marketplace / Connected App»,
но в КБ подтверждений нет — только интеграции (Amazon SP-API, SellerBoard).
**Вопрос:** есть ли на платформе концепция «магазина приложений» / подключаемых
сторонних приложений, или единственная модель внешних данных — «Integration»?
**Блокирует:** домены Integrations и Apps Marketplace (последний помечен NV).

---

## B. К tech lead / backend — жизненные циклы и статусы 🟡 P1

> Без ответов раздел Entity Lifecycle неполон (нет кодов/переходов).

### DM7. Supplier Search Request — свой жизненный цикл? 🟡 P1 (§11.13; ER #22,#26)
**Контекст:** поиск поставщика отражён статусами товара (TO_BUYER_FOR_RESEARCH →
BUYER_FOUND_SUPPLIER / SUPPLIER_WAS_NOT_FOUND), но не отдельным enum.
**Вопрос:** «запрос на поиск поставщика» — самостоятельная сущность со своими
статусами или проекция статусов Product/Idea?
**Блокирует:** Entity Catalog (Supplier Search Request); связи #22, #26.

### DM8. Batch lifecycle — числовые коды и переходы? 🟡 P1 (§11.19)
**Контекст:** в КБ только вкладки awaiting-send / sent / archive; числовых кодов
статусов партии нет.
**Вопрос:** какие enum-состояния у Batch и переходы (создание → подтверждение
отправки → в пути → принята)?
**Блокирует:** Entity Lifecycle (Batch).

### DM9. Support Ticket vs Feedback — разграничение и статусы Ticket? 🟡 P1 (§11.16)
**Контекст:** есть Support (тикеты, `TicketModal`) и отдельно `feedback` со
своими статусами (Новый / В обработке / Принято / Выполнено / Отклонено / Нужна
информация).
**Вопрос:** Support Ticket и Feedback — разные сущности? Какие статусы у тикета
поддержки (в КБ их нет)? Feedback — это обращения/жалобы или что-то ещё?
**Блокирует:** Entity Catalog (Support Ticket, Feedback); Lifecycle.

### DM10. Permission Preset — есть ли жизненный цикл? 🟡 P1 (§11.19)
**Контекст:** пресеты прав существуют (`PermissionsModal`, `/user-permissions`),
но статусов пресета в КБ нет.
**Вопрос:** у пресета разрешений есть состояния (draft/active/archived) или это
просто именованный набор без lifecycle?
**Блокирует:** Entity Lifecycle (Permission Preset).

### DM11. Milestone — к какой сущности крепится? 🟡 P1 (§11.17; ER #91)
**Контекст:** есть `milestones` (`createdById`), `MilestonesModal`, настройка
«Вехи» в Admin.
**Вопрос:** вехи привязаны к товару, идее, заказу или к процессу целиком? Что
это бизнес-объект — этапы прогресса чего?
**Блокирует:** Entity Catalog (Milestone); связь Milestone→? (#91).

### DM12. Voice of Customer — сущность или аналитический срез? 🟡 P1 (§11.15; ER #82)
**Контекст:** есть отчёт `VOICE` и поля PCX/NCX в инвентаре.
**Вопрос:** VoC — отдельная сущность (обращения покупателей) или производный
аналитический срез над Product?
**Блокирует:** Entity Catalog (Voice of Customer); связь #82.

### DM13. SKU / UPC / EAN — сущности или атрибуты? 🟡 P1 (§11.14; ER #2,#3)
**Контекст:** SKU встречается только в UI-строке `AMZ order ID, ASIN, SKU`;
UPC/EAN — в определении «Баркод».
**Вопрос:** SKU/UPC/EAN отслеживаются как самостоятельные объекты или это
атрибуты Product / Barcode?
**Блокирует:** Entity Catalog (SKU, Barcode); связи #2, #3.

---

## C. К product — границы фич и второстепенные сущности 🟢 P2

### DM14. Super Box — существует? 🟢 P2 (§11.8)
**Контекст:** в КБ термина нет; есть группировка/объединение коробок
(`GroupingBoxesModal`, `MergeBoxesModal`).
**Вопрос:** есть ли понятие «Super Box» (контейнер из коробок) или это только
операции группировки/мёржа над Box?
**Блокирует:** Entity Catalog (Super Box, помечен NV).

### DM15. Dashboard Widget — конфигурируемые виджеты? 🟢 P2 (§11.9; ER #80)
**Контекст:** дэшборд у каждой роли свой, но сущность «виджет» не подтверждена.
**Вопрос:** дэшборд состоит из настраиваемых виджетов (сущность Widget) или это
фиксированный набор блоков?
**Блокирует:** Entity Catalog (Widget, NV); связь Dashboard→Report (#80).

### DM16. Announcement — назначение и роли? 🟢 P2 (§11.18; ER #97)
**Контекст:** есть `announcements` (8 колонок), `SelectAnnouncementModal`,
фильтр `createdById != userId`.
**Вопрос:** что такое «объявление» на платформе (анонсы? объявления на бирже?),
кто создаёт и кому показывается?
**Блокирует:** Entity Catalog (Announcement); связь #97.

### DM17. Brand Launch — отдельный процесс/сущность? 🟢 P2 (§11.21)
**Контекст:** в wiki есть «Запуск бренда» отдельно от «Запуск продукта».
**Вопрос:** «запуск бренда» — отдельный процесс/сущность или частный случай
Product Launch (Idea)?
**Блокирует:** Entity Catalog (Brand); домен Product Research.

### DM18. Parent Product ↔ Variation — структура связи? 🟢 P2 (ER #8,#9)
**Контекст:** есть поле «Вариация», `addVariation`, `addParent`, `BindProductModal`.
**Вопрос:** как моделируется связь родитель↔вариации (parent ASIN + child ASIN)?
Вариация — отдельный Product или атрибут?
**Блокирует:** связи Product↔Variation, Variation↔Parent Product (#8, #9).

### DM19. Отчёты — нужны ли продуктовые определения? 🟢 P2 (§11.20)
**Контекст:** raw data_filters перечисляет ~23 типа отчётов (ORDERS, INCOME,
TRANSACTIONS, VOICE, FBA_INVENTORY, BUSINESS_REPORTS, ACCOUNT_HEALTH и др.);
в КБ они не расписаны.
**Вопрос:** какие из этих отчётов пользователь реально видит и стоит описать в
КБ как продуктовые сущности/статьи (а какие — служебные)?
**Блокирует:** домен Analytics; KB Mapping (DOMAIN_MODEL §9).

---

## D. Подтверждено — ответа не требуется (для контекста)

Терминологические расхождения уже подтверждены (пользователем/документацией),
в модели зафиксированы оба варианта — выносим только чтобы tech lead был в курсе:

| # | Факт | Статус |
|---|---|---|
| §11.1 | Freelancer (UI) = Service Provider (роуты/бэкенд) | подтверждено |
| §11.2 | Storekeeper (design) = «warehouse» (таблицы бэкенда) | подтверждено |
| §11.3 | Order status: текст (Glossary) vs числовые коды (ENTITY_STATES); канон = ENTITY_STATES | подтверждено |
| §11.4 | В источнике статусов подписи «Box Status» (=Idea) и «Task Priority» (=Strategy) даны неверно | подтверждено |
| §11 | Тестовые логины: e-mail смещены относительно ролей — использовать только `CODE→ROLE` | подтверждено |

> Опциональная сверка (не блокирует): `products` = 197 фильтруемых колонок vs
> ~180 определённых в глоссарии Инвентаря — расхождение за счёт вложенных/
> служебных полей (`inventory*`, `currentSupplierCard*`). Дозаполнить при желании.

---

## Сводка приоритетов

| Приоритет | Вопросы | Что разблокирует |
|---|---|---|
| 🔴 P0 | DM1–DM6 | Каталог сущностей: что вообще является сущностью |
| 🟡 P1 | DM7–DM13 | Жизненные циклы, статусы, разграничение сущностей |
| 🟢 P2 | DM14–DM19 | Второстепенные сущности и границы фич |

**Как вносить ответы:** правим [DOMAIN_MODEL](DOMAIN_MODEL.md) (снимаем NV из
Entity Catalog + §11) и [ENTITY_RELATIONSHIPS](ENTITY_RELATIONSHIPS.md)
(проставляем кардинальность, меняем статус на Confirmed), при необходимости —
[GLOSSARY](GLOSSARY.md) и [ENTITY_STATES](ENTITY_STATES.md). Этот файл — рабочий
трекер; закрытые вопросы помечаем ✅ с датой ответа.
