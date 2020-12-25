## Тех. карта
Средствами JSON API можно создавать и обновлять сведения о Тех. картах, запрашивать списки Тех. карт и сведения по отдельным Тех. картам. Позициями Тех. карт можно управлять как в составе отдельной Тех. карты, так и отдельно - с помощью специальных ресурсов для управления материалами и продуктами Тех. карты. Кодом сущности для Тех. карты в составе JSON API является ключевое слово **processingplan**. Больше о Тех. картах и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки по
[этой ссылке](https://support.moysklad.ru/hc/ru/articles/203325613-%D0%A1%D0%B1%D0%BE%D1%80%D0%BE%D1%87%D0%BD%D1%8B%D0%B5-%D0%B8-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8).
### Тех. карты 
#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**meta**               |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Тех. карты|&mdash;|да
|**id**                 |UUID|ID Тех. карты|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**updated**            |DateTime|Момент последнего обновления Тех. карты|Только для чтения|да
|**deleted**            |DateTime|Момент последнего удаления Тех. карты|Только для чтения|нет
|**name**               |String(255)|Наименование Тех. карты|Необходимое при создании|да
|**externalCode**       |String(255)|Внешний код Тех. карты|&mdash;| да
|**owner**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Владелец (Сотрудник)|&mdash;|да
|**shared**             |Boolean|Общий доступ|&mdash;|да
|**group**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Отдел сотрудника|&mdash;|да
|**pathName**       |String|Наименование группы, в которую входит Тех. карта|Только для чтения| да
|**parent**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные группы Тех. карты|&mdash;|да
|**cost**                |Int| Стоимость производства|&mdash;|нет
|**processingprocess**         |([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Метаданные процесса Техкарты|Необходимое при создании|да
|**processingStages**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных этапов Техкарты|Только для изменения количественных характеристик|да
|**materials**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных материалов Техкарты|Необходимое при создании|да
|**products**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных готовых продуктов Техкарты|Необходимое при создании|да
|**costDistribution**         |String|Тип распределения себестоимости, может принимать значения "price" или "percent"|По умолчанию создается с типом распределения по ценам продаж|да

#### Материалы Тех. карты
Материалы Тех. карты - это список товаров, используемых для производства готовых продуктов.
Объект материала Тех. карты содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Материала|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**product**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара позиции|&mdash;|нет
|**processingStage**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные этапа, на котором произойдет списание материала|&mdash;|нет
|**quantity**               |Int|Количество товаров данного вида в позиции|&mdash;|да

#### Продукты Тех. карты
Продукты Тех. карты - это список товаров, получаемых при производстве.
Объект продукта Тех. карты содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Продукта|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**product**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара позиции|&mdash;|нет
|**quantity**               |Int|Количество товаров данного вида в позиции|&mdash;|да
|**costShare**               |Int|Процентное распределение себестоимости в случае если выбран тип распределений себестоимости в процентах|&mdash;|да

#### Этапы Техкарты
Этапы Техкарты - это список этапов Техкарты, из которых состоит связанный производственный процесс. Материалы привязываются к этапам
Объект этапа Техкарты содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Продукта|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**processingStage**    |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные этапа|&mdash;|нет
|**cost**               |Int|Материальные затраты на производстве|&mdash;|да
|**salary**             |Int|Сумма сдельной заработанной платы за прохождение этапа исполнителем|&mdash;|нет
|**personified**        |Boolean|Требование к тому, чтобы при прохождении этапа был указан пользователь, который этот этап реализовал|&mdash;|да

С материалами и продуктами можно работать с помощью [специальных ресурсов для управления позициями Тех. карты](../documents/#dokumenty-teh-karta-materialy-teh-karty),
а также в составе отдельной Тех. карты. При работе в составе отдельной Тех. карты,
вы можете отправлять запросы на создание отдельной Тех. карты с включенными в тело запроса
массивами материалов и продуктов Тех. карты. Если количество материалов или продуктов превышает максимально допустимое, то для
дальнейшего пополнения материалов и продуктов нужно будет работать со специальнымы ресурсами "Материалы Тех. карты" и "Продукты Тех. карты".
Также, при работе в составе отдельной Тех. карты, можно отправлять запросы на обновление списка материалов и продуктов
с включенными в тело запроса массивами материалов и продуктов Тех. карты. При этом важно помнить, что коллекции материалов и продуктов
полностью заменят уже существующие коллекции при обновлении объекта - лишние
позиции будут удалены, новые добавлены, существующие - изменены.

### Тех. карта

### Получить Тех. карту

**Параметры**

|Параметр   |Описание   |
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Техкарты.|

> Запрос на получение отдельной Тех. карты с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingplan/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Тех. карты.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/1a18770e-ad9a-11e6-5bed-427b00000064",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
    "type": "processingplan",
    "mediaType": "application/json"
  },
  "id": "1a18770e-ad9a-11e6-5bed-427b00000064",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-21 14:55:08",
  "name": "Тех. карточка",
  "externalCode": "4geOQkq5h7d5w1-tUATmt3",
  "pathName": "",
  "cost": 1000,
  "processingStages": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/1a18770e-ad9a-11e6-5bed-427b00000064/procesingStages",
      "type": "processingplanstage",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  },
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/1a18770e-ad9a-11e6-5bed-427b00000064/materials",
      "type": "processingplanmaterial",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/1a18770e-ad9a-11e6-5bed-427b00000064/products",
      "type": "processingplanresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}

```
