# Entity States — коды и статусы сущностей

> Канонический справочник enum-значений Seller Exchange (внутр. **AmazonService
> / AS**): коды ролей, статусы товара/заказа/коробки/партии, типы задач и др.
> Источник правды для жизненных циклов в [WORKFLOW_CATALOG](WORKFLOW_CATALOG.md),
> статусов в [GLOSSARY](GLOSSARY.md), кодов ролей в
> [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md).
>
> Первоисточник: Google Sheet «Entities & Scenarios»
> (`1rlZhGJj7_yS-b6uc0ARFswzUFZYQOoDCuxqE2wDwGyA`). Значения (`CODE`, `NAME`) —
> бэкенд-идентификаторы, **не переводятся**; описания на RU.
>
> 🔒 Лист содержит тестовые логины с паролями — они намеренно **не** внесены в
> базу знаний (секреты не документируем). Здесь только маппинг кодов ролей.

## Коды ролей (Role codes)

| CODE | ROLE | RU | В [PERMISSIONS_MATRIX](PERMISSIONS_MATRIX.md) |
|---|---|---|---|
| 0 | ADMIN | Админ | Admin |
| 10 | CLIENT | Клиент | Client |
| 20 | SUPERVISOR | Супервайзер | Supervisor |
| 30 | RESEARCHER | Ресечер | Researcher |
| 35 | FREELANCER | Фрилансер | Freelancer (routes: Service Provider) |
| 40 | BUYER | Байер | Buyer |
| 45 | STOREKEEPER | Сторкипер | Storekeeper |
| 50 | CANDIDATE | Кандидат | Candidate |
| 60 | MODERATOR | Модератор | Moderator |

> ℹ️ Достоверен маппинг `CODE→ROLE` выше. В листе-источнике e-mail тестовых
> аккаунтов смещены относительно ролей (напр. `researcher@gmail.com` → CLIENT) —
> это особенность тестовых данных, пары «почта↔роль» не используем.

## Статусы товара / карточки (Product status)

Жизненный цикл карточки продукта. Ветка `0–110` — стандартный поток
(Researcher → Supervisor → Buyer → биржа); ветка `200–300` — «от клиента»
(`FROM_CLIENT_*`), когда инициатор — Client.

| CODE | NAME | Описание |
|---|---|---|
| 0 | NEW_PRODUCT | Ресёрчер создал продукт |
| 5 | RESEARCHER_CREATED_PRODUCT | Ресёрчер отправил на проверку супервайзеру |
| 10 | RESEARCHER_FOUND_SUPPLIER | Отправлено супервайзеру с поставщиком |
| 15 | CHECKED_BY_SUPERVISOR | Проверено супервайзером (товар подходит) |
| 20 | REJECTED_BY_SUPERVISOR_AT_FIRST_STEP | Отклонено супервайзером |
| 25 | TEMPORARILY_DALAYED | Временно отклонён |
| 30 | TO_BUYER_FOR_RESEARCH | Передано байеру на поиск поставщика |
| 35 | BUYER_PICKED_PRODUCT | Байер взял в работу |
| 40 | BUYER_FOUND_SUPPLIER | Байер нашёл поставщика |
| 50 | SUPPLIER_WAS_NOT_FOUND_BY_BUYER | Байер не нашёл поставщика |
| 60 | SUPPLIER_PRICE_WAS_NOT_ACCEPTABLE | Цена поставщика не подходит |
| 70 | COMPLETE_SUCCESS | Проверено супервайзером и опубликовано |
| 75 | PURCHASED_PRODUCT | Куплен клиентом, оплачен |
| 80 | COMPLETE_SUPPLIER_WAS_NOT_FOUND | Поставщик не найден (проверено супервайзером) |
| 90 | COMPLETE_PRICE_WAS_NOT_ACCEPTABLE | Цена не подходит (проверено супервайзером) |
| 100 | NO_PUBLISHED | Скрытие товара с биржи админом |
| 110 | PLATFORMS_FREE | Принадлежит платформе, распространяется бесплатно |
| 200 | CREATED_BY_CLIENT | Создан клиентом |
| 205 | FROM_CLIENT_READY_TO_BE_CHECKED_BY_SUPERVISOR | Отправлен клиентом супервайзеру |
| 230 | FROM_CLIENT_TO_BUYER_FOR_RESEARCH | Передано байеру на поиск |
| 235 | FROM_CLIENT_BUYER_PICKED_PRODUCT | Байер взял в работу |
| 240 | FROM_CLIENT_BUYER_FOUND_SUPPLIER | Байер нашёл поставщика |
| 250 | FROM_CLIENT_SUPPLIER_WAS_NOT_FOUND_BY_BUYER | Байер не нашёл поставщика |
| 260 | FROM_CLIENT_SUPPLIER_PRICE_WAS_NOT_ACCEPTABLE | Цена не подходит |
| 270 | FROM_CLIENT_COMPLETE_SUCCESS | Поиск завершён, проверено супервайзером |
| 275 | FROM_CLIENT_PAID_BY_CLIENT | Оплачено за поиск поставщика |
| 280 | FROM_CLIENT_COMPLETE_SUPPLIER_WAS_NOT_FOUND | Поставщик не найден |
| 290 | FROM_CLIENT_COMPLETE_PRICE_WAS_NOT_ACCEPTABLE | Цена не подходит |
| 300 | SUPPLIER_FOUND | Поставщик найден |

## Статусы заказа (Order status) — канонические

Уточняет текстовую цепочку из [GLOSSARY](GLOSSARY.md). Ветка `0–3` — отложенный
заказ (`FORMED`/`PENDING`/`READY_FOR_BUYOUT`), далее основной поток обработки
байером.

| CODE | NAME | Описание |
|---|---|---|
| 0 | FORMED | Создан отложенный заказ |
| 1 | NEW | Клиент создал заказ |
| 2 | PENDING | Байер взял в работу отложенный заказ |
| 3 | READY_FOR_BUYOUT | Отложенный заказ готов к выкупу |
| 10 | READY_TO_PROCESS | Доступен к обработке байером |
| 15 | AT_PROCESS | Байер взял заказ в обработку |
| 16 | READY_FOR_PAYMENT | Готов к оплате |
| 17 | PARTIALLY_PAYMENT | Частичная оплата |
| 19 | NEED_CONFIRMING_TO_PRICE_CHANGE | Нужно подтверждение клиента по доплате |
| 20 | PAID_TO_SUPPLIER | Оплачено поставщику |
| 25 | TRACK_NUMBER_ISSUED | Получен трек-номер |
| 27 | NEED_CONFIRMING_RECEIVING | Ожидает подтверждения байером |
| 30 | IN_STOCK | Товар пришёл на склад (выполнен) |
| 35 | CANCELED_BY_BUYER | Отменён байером |
| 40 | CANCELED_BY_CLIENT | Отменён клиентом |
| 45 | AWAITING_SHIPMENT | Ожидает отправки |
| 50 | SHIPPED | Отправлен |

## Типы заказа (Order type)

| CODE | NAME |
|---|---|
| 10 | LONG |
| 20 | STANDARD |
| 30 | URGENT |
| 40 | PROBLEMATIC |

## Статусы идеи / запуска товара (Product-launch status)

> ℹ️ В листе-источнике секция названа «Box Status», но фактически это статусы
> **идеи** (совпадают со вкладками Product Launch `/product-launch/*`), а не
> коробки. Подтверждено — используем как статусы идеи.

| CODE | NAME | Вкладка Product Launch |
|---|---|---|
| 5 | New | new-ideas |
| 10 | On checking | on-checking |
| 13 | Supplier search | supplier-search |
| 14 | Supplier found | — |
| 15 | Supplier not found | — |
| 16 | Card creating | create-card |
| 18 | Adding ASIN | adding-asin |
| 20 | Realized | realized-ideas |
| 25 | Rejected | rejected-and-closed |
| 30 | Closed | rejected-and-closed |

## Статусы товара на складе / отгрузки (Shipment status)

> ⚠️ В листе секция названа «Shipment Status»; описывает жизненный цикл
> товара/коробки на складах (преп-центр Китая → партия → преп-центр США).

| NAME | Описание |
|---|---|
| NEW | В пути на преп-центр Китая |
| ACCEPTED_IN_PROCESSING | Принято на склад, в обработке |
| IN_STOCK | На складе |
| REQUESTED_SEND_TO_BATCH | Запрошена в партию |
| NEED_CONFIRMING_TO_DELIVERY_PRICE_CHANGE | Нужно подтвердить новую цену тарифа |
| NEED_TO_UPDATE_THE_TARIFF | Нужно выбрать тариф (старый неактуален) |
| IN_BATCH | Ожидает отправления в партии |
| IN_BATCH_ON_THE_WAY | Отправлена в партии |
| FINISH_PREP_CENTR_USA | Принята на складе преп-центра США |

## Статусы карточки товара пользователя (Inventory item status)

> Подтверждено (DM2, 2026-07-01): **Inventory Item = Product** — карточка товара
> пользователя в его Инвентаре, за которой он закрепляет ASIN. Эти статусы
> отражают состояние карточки **в связке с Supplier Card** (предложением
> поставщика, купленным на бирже и привязанным к карточке). Цвет — индикация в UI.

| STATUS | RU | Цвет |
|---|---|---|
| VACANT | Свободный | Синий |
| RESERVED | Зарезервирован | Жёлтый |
| WAITING_INVITE | Ожидает приглашения | Жёлтый |
| INVITED | Приглашение получено | Жёлтый |
| REGISTERED | Зарегистрирован | Жёлтый |
| READY_TO_CHECKING | Готов к проверке | Жёлтый |
| IN_USE | Используется | Зелёный |
| UNLINKED | Не связан | Серый |

## Типы складских задач (Task type)

| CODE (name) | RU |
|---|---|
| receive | Принятие |
| edit | Редактирование |
| storekeeperEditBoxes | Редактирование складом |
| split | Разделение |
| merge | Объединение |

## Стратегия сорсинга (Strategy)

> ℹ️ В листе-источнике секция названа «Task Priority», но фактически это
> **стратегии сорсинга** (совпадают с разделом СТРАТЕГИЯ в wiki; Wholesale —
> вес 40). Подтверждено — используем как стратегию.

| CODE | NAME |
|---|---|
| 0 | NONE |
| 10 | DROPSHIPPING |
| 20 | PRIVATE_LABEL |
| 30 | ONLINE_ARBITRAGE_CHINA |
| 40 | WHOLESALE_USA |
| — | STRATEGY |

## Бизнес-модель / публикация (Business model)

| CODE | NAME |
|---|---|
| 0 | DRAFT |
| 5 | ON_HOLD |
| 10 | PUBLISHED |

## Статус карточки поставщика (Supplier card status)

| NAME | Описание |
|---|---|
| IS_BEING_COLLECTED | Формируется |
| HAS_DISPATCHED | Отправлена |

## Статус обращения / фидбека (Feedback status)

| CODE | RU |
|---|---|
| 10 | Новый |
| 20 | В обработке |
| 30 | Принято |
| 35 | Выполнено |
| 40 | Отклонено |
| 50 | Нужна информация |

## Правила ведения

- Значения `CODE`/`NAME` — точные бэкенд-идентификаторы, не переименовывать.
- При изменении enum правим здесь, затем зависимые статьи и глоссарий.
- Расхождения между подписью в источнике и фактическим смыслом помечаем `⚠️`
  и не «исправляем» молча (см. [CONTRIBUTING](CONTRIBUTING.md)).
