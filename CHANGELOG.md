# JSON API 1.3 Changelog
Изменения в JSON API 1.3 будут описаны в данном документе.

## 30-09-2021
### Изменено
- Информация о новом типе маркированной продукции (Упакованная вода) в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 23-09-2021
### Добавлено
- Описание полей посылаемых [веб-хуков](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-veb-huki) и добавлены поля `auditContext`, `updatedFields`, `moment`, `uid`
- Новая ошибка [30009](https://dev.moysklad.ru/doc/api/remap/1.2/#mojsklad-json-api-oshibki-kody-oshibok-dlq-veb-hukow)

## 20-09-2021
### Добавлено
- Добавлены поля `shipmentAddress` и `shipmentAddressFull` в [Заказ покупателя](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-zakaz-pokupatelq) и [Отгрузку](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-otgruzka)

## 20-09-2021
### Исправлено
- Исправлен список возможных атрибутов у документа [Списание](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-spisanie)

## 16-09-2021
### Изменено
- Дополнено описание раздела webhook.

## 15-09-2021
### Добавлено
- Поле `markingSellingMode` в [Точку продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)

## 15-09-2021
### Добавлено
- Возможность работы с упаковками [Модификаций](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-modifikaciq), [фильтрация ассортимента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-assortiment-izmenit-nastrojki-sprawochnika-kontragentow-atributy-dostupnye-dlq-fil-tracii) по штрихкоду упаковок модификаций.

## 15-09-2021
### Добавлено
- Добавлена фильтрация по Доп. полям. и атрибут фильтрации supplier для [Отчет обороты](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-oboroty)
- Документ [Корректировка баланса контрагента](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-korrektirowka-balansa-kontragenta)

## 19-08-2021
### Добавлено
- Создание розничной смены в позиции документов [Документов](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-sozdat-roznichnuu-smenu)
- Редактирование розничной смены в позиции документов [Документов](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-izmenit-roznichnuu-smenu)
- Добавлены поля `acquire`, `qrAcquire`, `bankPercent`, `qrBankPercent`,
  `bankComission`, `qrBankComission`   в розничную смену [Атрибуты розничной смены](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-atributy-smeny)
- Добавлен объект `cheque` с полями **start**, **end**
- Добавлен объект `start` с полями **fnNumber**, **kktRegNumber**, **fiscalDocSign**,
  **shiftNumber**, **fiscalDocNumber**, **time** в розничную смену [Поля объекта](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-informaciq-ob-otkrytii-smeny-kkt)
- Добавлен объект `end` с полями **fnNumber**, **kktRegNumber**, **fiscalDocSign**,
  **shiftNumber**,  **chequesTotal**, **fiscalDocNumber**, **fiscalDocsTotal**, **time** в розничную смену [Поля объекта](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-informaciq-o-zakrytii-smeny-kkt)
- Добавлен тип ошибок с кодом 12011, 12026 [ошибки](https://dev.moysklad.ru/mojsklad-json-api-oshibki-kody-oshibok-dlq-roznichnyh-smen-pos)

## 19-08-2021
### Изменено
- Удалено поле `agent` в розничной смене [Атрибуты розничной смены](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-atributy-smeny)
- Исправлено описание `updated`, `name`, `description`, `externalCode`, `moment`, `organization`, `store`,
  `attributes`, `published`, `closeDate`, `retailStore` в атрибутах розничной смены [Атрибуты розничной смены](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-atributy-smeny)
  
## 17-08-2021
### Добавлено
- Возможность работы с модификациями для материалов и продуктов [Тех. карт](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-teh-karta). 
Для этого введено новое поле **assortment**.
- Новая ошибка [3028](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-obschie-oshibki-walidacii)

## 30-07-2021
### Добавлено
- Добавлены атрибуты фильтрации type и withoutturnover для [Отчет обороты](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-oboroty)

## 29-07-2021
### Добавлено
- [Фильтрация ассортимента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-assortiment-izmenit-nastrojki-sprawochnika-kontragentow-atributy-dostupnye-dlq-fil-tracii) по штрихкоду, наименованию группы товаров, типу и использованию серийных номеров

## 28-07-2021
### Добавлено
- Возможность работать с файлами в комментариях к [задачам](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-zadacha)

## 28-07-2021
### Добавлена
- Возможность expand поля **masterRetailStores** у [точек продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)

## 26-07-2021
### Изменено
- Добавлено поле `useParentVat` в [Группы товаров](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-gruppa-towarow), [Товары](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar), [Комплекты](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/№suschnosti-komplekt), [Услуги](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-usluga)

## 09-07-2021
### Добавлено
- Новый ресурс [Обороты по товару с детализацией по документам](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-oboroty-oboroty-po-towaru-s-detalizaciej-po-dokumentam)

## 01-07-2021
### Исправлено
- Исправлено описание обязательности полей отчета обороты при ответе

## 28-06-2021
### Добавлено
- Пермиссии на документы маркировки в [правах сотрудника](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik-rabota-s-prawami-sotrudnika)

## 25-06-2021
### Добавлено
- Новый ресурс [Отчет обороты](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-oboroty)

## 10-06-2021
### Документация
- Добавлено описание параметров фильтрации выборки `momentFrom` и `momentTo` в отчетах прибыльности

## 03-06-2021
### Документация
- Исправлено описание атрибута `pack` у позиций документов

## 03-06-2021
### Добавлено
- Возможность перехода к соответствующему разделу с описанием ошибки по ссылке в `errors.moreInfo`

## 01-06-2021
### Добавлено
- Возможность получать и изменять пользовательские роли от лица приложения
- Исправлена ошибка: при изменении пермиссий у роли сотрудника, был невозможен вход в систему

## 31-05-2021
### Добавлено
- Добавлены поля `welcomeBonusesEnabled`, `welcomeBonusesValue`, `welcomeBonusesEnabled` в [Бонусную программу](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-bonusnaq-programma)

## 28-05-2021
### Документация
- Добавлена колонка `Expand` в таблицы описания атрибутов сущностей в разделах: "Сущности" и "Документы"

## 27-05-2021
### Добавлено
- Добавлены новые поля `authorizedHosts`, `authorizedIpNetwork`, `authorizedIpNetmask` для ограничения доступа по ip в [эндпоинте управления правами сотрудника](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik-rabota-s-prawami-sotrudnika)

## 21-05-2021
### Документация
- Исправлено описание пермиссий при работе с пользовательскими справочниками

## 21-05-2021
### Добавлено
- Исправлена отметка об обязательности складов для части документов
- Добавлен новый эндпоинт для системных ролей
- Добавлен новый эндпоинт (crud) для пользовательских ролей
- Новый ресурс [отмены асинхронной задачи](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen-otmena-asinhronnoj-zadachi)
- Ошибка [61007](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-asinhronnogo-obmena)

## 20-05-2021
### Добавлено
- Добавлена возможность редактировать поле discounts у контрагента
- Раскомплектовывание комплектов на составляющие компоненты при создании [шаблона заказа поставщику на основе](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-zakaz-postawschiku-shablon-zakaza-postawschiku-na-osnowe)
- Добавлена новая схема работы с ошибками и новый статус `API_ERROR` в
  [асинхронныом обмене](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)

## 17-05-2021
### Документация
- В Позиции Отгрузки добавлен список комплектов
- Исправлено описание `product.packs.barcodes`, `consignment.barcodes`, `bundle.components`, `consignment.image`
- Исправлено описание атрибута `images` в товарах, комплектах и модификациях
- Исправлено указание на обязательность в ответе полей `uom.accountId`, `uom.group`, `product.minimumBalance`, `country.accountId`, `demand.vatSum`, `counterparty.state`
- Исправлено указание на обязательность в ответе поля `owner` в сущностях

## 12-05-2021
### Исправлено
- В примерах исправлен url получения метаданных [Комплектов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-komplekt)
  и [Услуг](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-usluga)

## 11-05-2021
### Добавлено
- Возможность выполнять запрос [получения Ассортимента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-assortiment)
 [асинхронно](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)

## 05-05-2021
### Добавлено
- Информация о новом типе маркированной продукции (Молочная продукция) в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)
  
## 29-04-2021
### Добавлено
- Возможность выполнять запрос [получения списка Контрагентов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-kontragent-poluchit-spisok-kontragentow)
 [асинхронно](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)

## 28-04-2021
### Документация
- Добавлен новый раздел [Подписка компании](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-podpiska-kompanii)

## 28-04-2021
### Изменено
- Для атрибутов
  AttributeMetadata.required ,
  AgentAccount.isDefault, WebHook.enabled, Product.weighed
  при передаче null значения выводится ошибка 2016

## 28-04-2021
### Изменено
- Исправлена работа с документом [Возврат поставщику](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-vozwrat-postawschiku): 
 добавлена проверка совпадения значения поля `vatEnabled` при создании и обновлении документа на основании [Приемки](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-priemka)

## 28-04-2021
### Изменено
- Для документа [`Оприходования`](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-oprihodowanie)
теперь учитывается пермиссия `Видеть себестоимость, цену закупки и прибыль товаров`. При отсутствии пермисcии в json представлении 
документа будет отсутствовать поле `sum`, а в позициях не будет поля `price`.

## 27-04-2021
### Добавлено
- Очередь для [асинхронных задач](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)
- Обновлен список [ограничений](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq-ogranicheniq) (добавлена информация про размер очереди асинхронных задач)
- Новый статус `PENDING` для [асинхронных задач](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)
- Эндпоинт получения [списка статусов асинхронных задач](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen-statusy-asinhronnyh-zadach)
- Поле **meta** для [асинхронных задач](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)

## 27-04-2021
### Добавлена
- Возможность создавать [вебхуки](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-veb-huki) для [асинхронных задач](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen-vebhuki-asinhronnoj-zadachi)

## 23-04-2021
### Добавлено
- Приложение как автор [Задач](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-zadacha) и [Событий Контрагента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-kontragent-sobytiq-kontragenta)

## 22-04-2021
### Документация
- Добавлено описание поля **code** для ряда сущностей. Где оно было, убран атрибут `Только для чтения`

## 15-04-2021
### Добавлено
- Возможность работы с файлами, прикрепленными к [Задаче](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-zadacha)

## 13-04-2021
### Добавлено
- Добавлена новая ошибка [17020](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-dokumentow) - товар из упаковки в позиции документа не соответствует товару, указанному в данной позиции
- Добавлена валидация товара из упаковки в позиции документа

## 09-04-2021
### Документация
- Переработан раздел [Работа с доп. полями](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)
- Добавлен тип MetaArray - объект с полями **meta** и **rows**
- Упоминание Array(Meta) изменено на Array(Object) или на MetaArray
- Изменен формат описания поля **trackingCodes** в Отгрузках и Приёмках
- Добавлен раздел [Валюта в документах](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-obschie-swedeniq-valuta-w-dokumentah) с описанием поля **rate**
- В описание добавлены отсутствовавшие поля **meta** в Счета и Контактные лица Контрагента
- Убрано возможное разночтение в описании поля **tags** Контрагента
- Для полей **consignee** и **carrier** в Отгрузках и Счетах-фактурах выданных добавлена пометка про тип сущностей
- Удалена пометка об обязательности поля **house** в адресах
- Исправлен тип поля **certificateNumber** у Юрлиц на корректный
### Изменено
- Изменен регистр ключевого слова в [заказе покупателя](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-zakaz-pokupatelq)
- Изменен регистр ключевого слова в [заказе поставщику](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-zakaz-postawschiku)

## 07-04-2021
### Добавлено
- Добавлен [пример](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-ostatki-dostup-k-otchetu-ostatki) в отчет остатки по параметру includeRelated 

## 06-04-2021
### Добавлено
- Добавлено [описание](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-pribyl-nost-poluchit-pribyl-nost-po-towaram) отчета по прибыльности по товарам
- Добавлено [описание](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-pribyl-nost-poluchit-pribyl-nost-po-modifikaciqm) отчета по прибыльности по модификациям

## 05-04-2021
### Изменено
- Обновлена информация об [ошибке](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki) **17102**

## 01-04-2021
### Добавлено
- Возможность выполнять запросы [асинхронно](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-asinhronnyj-obmen)
- Cтатья в [воркбук](https://dev.moysklad.ru/doc/api/remap/1.3/workbook/#workbook-rabota-s-asinhronnym-obmenom) 
- Описание ошибок [61000-61006](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-asinhronnogo-obmena)

## 29-03-2021
### Добавлено
- Поле `earnWhileRedeeming` в [Бонусную программу](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-bonusnaq-programma)

## 23-03-2021
### Добавлено
- Поле `postponedBonusesDelayDays` в [Бонусную программу](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-bonusnaq-programma)
- Поля `transactionStatus`, `executionDate` и `categoryType` в [Бонусные операции](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-bonusnaq-operaciq)

## 02-03-2021
### Добавлено
- Флаг `partialDisposal` для сущностей `Товар` и `Комплект`
- Ошибка `16112` с описанием

## 01-03-2021
### Документация
- Исправлен запрос в примере на [массовое удаление модификаций](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-modifikaciq-massowoe-udalenie-modifikacij)

## 11-02-2021
### Изменено
- Исправлены битые ссылки в [Общих сведениях](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq)
- Исправлено указание на обязательность в ответе поля `vatIncluded` в документах

## 04-02-2021
### Изменено
- Добавлен новый тип уведомлений [Уведомление из сценария](https://dev.moysklad.ru/doc/api/remap/1.3/other/#uwedomleniq-podrobnoe-opisanie-tipow-uwedomlenij-uwedomlenie-iz-scenariq)
- Добавлена новая группа уведомлений [Сценарии](https://dev.moysklad.ru/doc/api/remap/1.3/other/#uwedomleniq-nastrojki-uwedomlenij-atributy-suschnosti)

## 02-02-2021
### Добавлено
- Добавлены новые [эндпоинты для упралвения правами сотрудника](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik-rabota-s-prawami-sotrudnika) и [эндпоинты для доступа сотрудника к основному сервису 
МойСклад](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik-aktiwaciq-sotrudnika) в раздел [Сотрудники](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik)
- Добавлены новые ошибки [3023-3024](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-obschie-oshibki-walidacii) и [43007-43029](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-sotrudnikow)

## 27-01-2021
### Документация
- Изменен тип поля quantity с Int на Float в разделе описания вложенной [Упаковки товара](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar-towary-atributy-wlozhennyh-suschnostej-upakowki-towara)
- Все разделы распределены по соответствующим пакетам
- Удалено описание полей объекта доп. полей из документов. 
  Его по-прежнему можно найти в разделе [Работа с доп. полями](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)
- Исправлен ряд опечаток в списке изменений

## 20-01-2021
### Изменено
- Добавлены поля `printed` и `published` в [документах](https://dev.moysklad.ru/doc/api/remap/1.3/documents/)

## 18-01-2021
### Изменено
- Для доступа к аудиту не нужно быть администратором

## 23-12-2020
### Добавлено
- Новый эндпоинт [Настроек пользователя](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-nastrojki-pol-zowatelq)

## 22-12-2020
### Документация
- Из параметров удален `states`, добавленные туда по ошибке в [метаданных Розничных смен](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-smena-metadannye-roznichnyh-smen)
### Изменено
- Исправлены неточности в разделе [Отчет остатки](https://dev.moysklad.ru/doc/api/remap/1.3/reports/#otchety-otchet-ostatki)
- Описание ограничений в [воркбуке](https://dev.moysklad.ru/doc/api/remap/1.3/workbook/#workbook)
- Исправлен http метод в запросе на удаление группы товаров с GET на DELETE в [Группа товаров](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-gruppa-towarow-udalit-gruppu-towarow)
  и тип полей `minPrice`, `buyPrice` c Double на Object в [Товаре](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 21-12-2020
### Добавлено
- добавлен код [ошибки 14012](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-dop-polq)

## 17-12-2020
### Изменено
- Исправлен тип qrBankPercent с Int на Double в [Точке продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)

## 26-11-2020
### Изменено
- Исправлен некорректный url в примерах json [Управления настройками справочника ассортимента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-assortiment-poluchit-nastrojki-sprawochnika-towarow)

## 26-11-2020
### Добавлено
- Фильтрация по `assortment` для [Документов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#mojsklad-json-api-obschie-swedeniq-fil-traciq-wyborki-s-pomosch-u-parametra-filter-poluchenie-nowogo-tokena-dopolnitel-nye-fil-try)

## 12-11-2020
### Добавлено
- Поле `tobaccoMrcControlType` в [Точку продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)

## 05-11-2020
### Добавлено
- Эндпоинт [Управления настройками справочника контрагентов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-kontragent-nastrojki-sprawochnika-kontragentow)

## 02-11-2020
### Добавлено
- добавлены коды [ошибкок 1083, 1084](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-oshibki-formata).

## 29-10-2020
### Добавлено
- Исправлена ошибка регистра кода сущности в  [Группе товаров](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-gruppa-towarow)

## 23-10-2020
### Добавлено
- Поля `idQR` и `qrTerminalId` в [Точку продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)

## 21-10-2020
### Добавлено
- Информация о новых типах маркированной продукции (Альтернативная табачная продукция) в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 21-10-2020
### Изменено
- Добавлена возможность создавать, изменять и удалять [Отделы](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-otdel)

## 21-10-2020
### Добавлено
- Добавлено заполнение себестоимости в эндпоинт [Автозаполнения](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#pereschet-raschetnogo-ostatka-w-inwentarizacii-awtozapolnenie

## 21-10-2020
### Изменено
- Описание ограничений в [Общих сведениях](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq)

## 20-10-2020
### Добавлено
- Поля `qrPayEnabled`, `qrBankPercent` и `qrAcquire` в [Точку продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)
- Поля `qrSum` и `prepaymentQrSum` в [Розничную продажу](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-prodazhai)
- Поле `qrSum` в [Розничный возврат](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnyj-wozwrat)
- Ошибки `18005`, `18006`, `19003` и `19004`
### Изменено
- Описание полей `acquire` и `bankPercent` в [Точке продаж](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-tochka-prodazh)
- Описание [работы с полями оплаты розничной продажи](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-roznichnaq-prodazha-roznichnye-prodazhi-rabota-s-polqmi-oplaty-roznichnoj-prodazhi)
- Текст ошибок `18000` и `19002`

## 16-10-2020
### Добавлено
 - Эндпоинт [Автозаполнения цен, скидок, ндс позиций](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#pereschet-raschetnogo-ostatka-w-inwentarizacii-awtozapolnenie)
 - Описание ошибок [1084 и 56000](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki)

## 08-10-2020
### Изменено
- Исправлены опечатки

## 22-09-2020
### Исправлено
- Описание поля `productFolder` у [Групп товаров](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-gruppa-towarow)

## 20-09-2020
### Изменено
- Изменено описание установленных ограничений в [Общих сведениях](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq)

## 19-09-2020
### Добавлено
- Информация о новом типе маркированной продукции (Шины и покрышки) в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 18-09-2020
### Добавлены
- Новые поля `directorPosition`, `directorSign`, `chiefAccountSign`, `stamp` в [Юрлице](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-jurlico)

## 16-09-2020
### Добавлено
- Информация о новых типах маркированной продукции (духи и фотокамеры) в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 08-09-2020
### Добавлено
- Добавлена информация об ошибке **1090**

## 01-09-2020
### Добавлено
- Информация о новых типах маркированной продукции в [Товарах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar)

## 13-08-2020
### Изменено
- Обновлена информация об ошибке **17102**

## 04-08-2020
### Добавлено
- Дополнена информация об ошибке **17102**

## 30-07-2020
### Изменено
Дополнительные поля Товаров, Услуг, Модификаций и Комплектов объединены и располагаются в метаданных Товаров.

## 28-07-2020
### Добавлено
- Добавлена возможность изменять настройки применения скидок в настройках компании

## 27-07-2020
### Добавлено
 - Поля `minionToMasterType` и `masterRetailStores` в точку продаж, позволяющие указывать стратегию выбора мастер точки продаж для фискализации облачных чеков.
 
## 24-07-2020
### Добавлено
- Новая ошибка 1083 - ошибка формирования ответа на стороне сервера
- Новый формат описания атрибутов сущностей с помощью таблиц

## 22-07-2020
### Добавлено
 - Поле `factureIn` для [возврата поставщику](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-vozwrat-postawschiku), представляющее собой ссылку на связанный с возвратом [счет-фактуру полученный](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-schet-faktura-poluchennyj)
 
## 09-07-2020
### Добавлено
 - Описание кодов маркировки пользовательской упаковки (КМ ПУ) в сущностях [`Отгрузка`](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-otgruzka) и [`Приемка`](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-priemka)
 - Ошибки при импорте КМ ПУ из xml  
 - Поле [factureOut](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-vozwrat-pokupatelq-vozwraty-pokupatelej-swqzi-s-drugimi-dokumentami) для возврата поставщику, представляющее собой ссылку на связанный с возвратом счет-фактуру выданный

## 08-07-2020
### Добавлено
 - Поле `ppeType` (код средства индивидуальной защиты) [в сущность `Товары`](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar-towary-atributy-suschnosti).

## 07-07-2020
### Добавлено
 - [Фильтрация комплектов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-assortiment-udalit-sobytie-atributy-dostupnye-dlq-fil-tracii) по артикулу в ассортименте

## 26-06-2020
### Добавлено
 - Раздел про [получение токена](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq-autentifikaciq-poluchenie-nowogo-tokena) дополнен информацией про отзыв прошлых токенов при создании нового
### Исправлено
 - В примерах исправлен заголовок авторизации через токен

## 18-06-2020
### Добавлено
 - Поля ФИО для [Юрлиц](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-jurlico) и [Контрагентов](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-kontragent) типа индивидуальный предприниматель и физическое лицо
 - Добавлена возможность работы с [файлами](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-fajly) и поле `files` в сущностях и документах
 
## 11-06-2020
### Исправлено
 - Информация о лимитах на число элементов в коллекциях и вложенных сущностях ([1000 элементов](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-obschie-swedeniq-sozdanie-i-obnowlenie-neskol-kih-ob-ektow))

## 28-05-2020
### Добавлено
 - Добавлена информация о таймаутах и новом [параметре в Вебхуках](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-veb-huki)

## 28-05-2020
### Добавлено
 - [Ошибки 16102-16110](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-towarow), связанные с маркированными товарами

## 15-05-2020
### Добавлено
 - Пояснение об ограничениях при изменении [атрибутов сотрудника](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik-sotrudniki-atributy-suschnosti)

## 08-05-2020
### Добавлено
 - Описание работы с маркированными товарами в [приемке](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-priemka-priemki-pozicii-priemki) и [отгрузке](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-otgruzka-otgruzki-pozicii-otgruzki)
 
## 07-05-2020
### Добавлено
 - Описание [эндпоинта работы с характеристиками модификаций](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-harakteristiki-modifikacij)
 - [Ошибка 10002](https://dev.moysklad.ru/doc/api/remap/1.3/#mojsklad-json-api-oshibki-kody-oshibok-dlq-towarow) создания характеристик модификаций с существующим именем
### Исправлено
 - Описание [характеристик модификаций](https://dev.moysklad.ru/doc/api/remap/1.3/#suschnosti-modifikaciq-modifikacii-atributy-wlozhennyh-suschnostej-metadannye-modifikacij-harakteristiki-modifikacii) в разделе Модификации
