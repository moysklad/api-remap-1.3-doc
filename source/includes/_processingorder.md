## Заказ на производство
### Заказы на производство 
Средствами JSON API можно создавать и обновлять сведения о Заказах на производство, запрашивать списки Заказов и сведения по отдельным Заказам на производство. Позициями продукции и материалов Заказов можно управлять как в составе отдельного Заказа на производство, так и отдельно - с помощью специальных ресурсов для управления позициями Заказа. Кодом сущности для Заказа на производство в составе JSON API является ключевое слово **processingorder**. Больше о Заказах на производство и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки по [этой ссылке](https://support.moysklad.ru/hc/ru/articles/203325613-%D0%A1%D0%B1%D0%BE%D1%80%D0%BE%D1%87%D0%BD%D1%8B%D0%B5-%D0%B8-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8).
#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**meta**               |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Заказа на производство|Только для чтения|да
|**id**                 |UUID|ID Заказа на производство|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**syncId**             |UUID|ID синхронизации. После заполнения недоступен для изменения|Только для чтения|нет
|**updated**            |DateTime|Момент последнего обновленияЗаказа на производство|Только для чтения|да
|**deleted**            |DateTime|Момент последнего удаления Заказа на производство|Только для чтения|нет
|**name**               |String(255)|Наименование Заказа на производство|Необходимое при создании|да
|**description**        |String(4096)|Комментарий Заказа на производство|&mdash;|нет
|**externalCode**       |String(255)|Внешний код Заказа на производство|Только для чтения| да
|**moment**             |DateTime|Дата документа|Только для чтения|да
|**applicable**         |Boolean|Отметка о проведении|&mdash;|да
|**project**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные проекта|&mdash;|нет
|**owner**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Владелец (Сотрудник)|&mdash;|да
|**shared**             |Boolean|Общий доступ|Только для чтения|да
|**group**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Отдел сотрудника|&mdash;|да
|**organization**       |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные юрлица|Необходимое при создании|да
|**store**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада материалов|Необходимое при создании|да
|**productStore**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада продукции|Необходимое при создании|да
|**state**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные статуса Заказа на производство|&mdash;|нет
|**organizationAccount**|[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные счета юрлица|&mdash;|нет
|**attributes**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных доп. полей. [Поля при expand'е](../documents/#dokumenty-zakaz-na-proizwodstwo-zakazy-na-proizwodstwo-atributy-suschnosti-polq-pri-expand-39-e-dop-polej) |Только для чтения|нет
|**files**              |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Массив метаданных [Файлов](../dictionaries/#suschnosti-fajly) (Максимальное количество файлов - 100)|&mdash;|да
|**created**            |DateTime|Дата создания|Только для чтения|да
|**productionRows**        |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Метаданные рядов продукции Заказа на производство|Необходимое при создании|нет
|**deliveryPlannedMoment**            |DateTime|Планируемая дата производства|&mdash;|нет

##### Поля при expand'е доп. полей
Описание полей при expand'е attributes

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**name**            |String(255)|Номер документа|&mdash;|нет
|**moment**          |DateTime|Дата печати|&mdash;|да
|**href**            |URL|Ссылка на файл печатной формы|&mdash;|да
|**fileName**        |String(255)|Название файла печатной формы|&mdash;|нет
|**updated**         |DateTime|Момент последнего обновления|&mdash;|да

#### Связи с другими документами
|Название          | Описание  |
| ------------------------------ |:---------------------------|
|**processings** | Массив ссылок на связанные тех. операции в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
|**manufactures** | Массив ссылок на связанные документы Производство в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

####  Ряды продукции по техкарте
Позиции Заказа - это список объектов, элемент которого включает в себя техкарту, список продукции по техкарте, список материалов по техкарте, список этапов по техкарте, материальные затраты на этапах, размер сдельной зп за выполнение этапа. Доступно добавление или удаление материалов, для продукции доступно только изменение количественных характеристик. Также доступно изменение всех количественных характеристик элементов внутри ряда продукции по техкарте через изменение объема производства. Важно: при изменении объема производства удаляются все материалы, которые не присутствуют в техкарте и были добавлены вручную. 
Объект позиции Заказа содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID позиции|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**processingPlan**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Тех. плана|Необходимое при создании|да
|**volume**          |Int|Объем производства|Изменение объема производства ведет за собой изменение всех связанных количественных характеристик по техкарте с множителем равным объему производства |да
|**costDistribution**          |String|Тип распределения себестоимость для ряда продукции по техкарте. Может принимать 2 значения: "price" - распределение по ценам продаж или "percent" - процентное распределение. |&mdash;|да
|**products**|Array(Object)|Список продукции по техкарте.|Доступны только количественные характеристики для изменения.|да
|**stages**|Array(Object)|Список этапов производства. Включается в себя |Доступны только количественные характеристики для изменения.|да

#### Продукция по техкарте внутри ряда продукции
| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID позиции|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**assortment**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара продукции|Необходимое при создании|да
|**quantity**          |Int|Количество товаров/услуг данного вида в позиции. Если позиция - товар, у которого включен учет по серийным номерам, то значение в этом поле всегда будет равно количеству серийных номеров для данной позиции в документе.|&mdash;|да
|**processingPlanQuantity**|Int|Количество товаров/услуг данного вида в позиции по техкарте.|&mdash;|да
|**percentDistribution**|Int|Процент распределения себестоимости в случае если задан тип распределения себестоимости по процентам|&mdash;|нет

#### Список этапов внутри ряда продукции
Объект этапа в рамках заказа на производство внутри себя также включает связанные материалы, и планируемую денежную часть: сдельная оплата труда исполнителю и денежные затраты на производство в рамках прохождения этапа производства связанного ряда продукции.

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID позиции|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**final**|Boolean|Определяет зачисление продукции этапом. Финальный этап для ряда продукции может быть только один|Только для чтения|да
|**name**|String|Наименование этапа|Только для чтения|да
|**personified**|Boolean|Является ли этап персонализированным. Если да, то при прохождении этапа необходимо указать исполнителя|Только для чтения|да
|**cost**|Int|Затраты на производство|&mdash;|да
|**salary**|Int|Размер сдельной оплаты труда исполнителю|&mdash;|нет
|**materials**|Array(Object)|Список материалов для этапа|Доступны только количественные характеристики для изменения|да

#### Список материалов для этапа внутри ряда продукции
| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**|          UUID|ID позиции|Только для чтения|да
|**accountId**|   UUID|ID учетной записи|Только для чтения|да
|**assortment**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара материала|Необходимое при создании|да
|**quantity**          |Int|Количество товаров/услуг данного вида в позиции. Если позиция - товар, у которого включен учет по серийным номерам, то значение в этом поле всегда будет равно количеству серийных номеров для данной позиции в документе.|&mdash;|да
|**processingPlanQuantity**|Int|Количество товаров/услуг данного вида в позиции по техкарте.|&mdash;|да
|**reserve**           |Int|Резерв данной позиции|&mdash;|да

С позициями можно работать с помощью специальных ресурсов для управления позициями Заказа,
а также в составе отдельного Заказа на производство. Добавление рядов продукции возможно только через отдельный эндпоинт. 
Также, при работе в составе отдельного Заказа на производство, можно отправлять запросы на обновление списка позиций
с включенным в тело запроса массивом позиций Заказа. Можно добавлять или удалять новые материалы внутрип этапа ряда продукции, но добавлять или удалять отдельные товары продукции невозможно. 

О работе с доп. полями Заказов на производство можно прочитать [здесь](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)

### Получить список Заказов на производство 
Запрос всех Заказов на производство на данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные о выдаче,
**context** | [Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye) | Метаданные о сотруднике, выполнившем запрос.
**rows** |Array(Object)|Массив JSON объектов, представляющих собой Заказы на производство.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|**limit** |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|**offset** |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|
|**search** |  `string` (optional) *Example: 0001* Фильтр документов по указанной поисковой строке.

> Получить список Заказов на производство

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка Заказов на производство.

```json
{
  "context": {
    "employee": {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/context/employee",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
        "type": "employee",
        "mediaType": "application/json"
      }
    }
  },
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorder",
    "mediaType": "application/json",
    "size": 1,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
        "type": "processingorder",
        "mediaType": "application/json"
      },
      "id": "c49e83b3-01af-11e6-9464-e4de00000026",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
      "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
      "updated": "2016-04-14 13:08:58",
      "name": "000034",
      "externalCode": "DAD9peGij6sDNii49Dkam2",
      "created": "2007-02-07 17:16:41",
      "owner": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": false,
      "group": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "moment": "2016-04-19 13:50:24",
      "applicable": false,
      "store": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
          "type": "store",
          "mediaType": "application/json",
          "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
        }
      },
      "productStore": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
          "type": "store",
          "mediaType": "application/json",
          "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
        }
      },
      "organization": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
          "type": "organization",
          "mediaType": "application/json"
        }
      },
      "state": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata/states/fb56c504-2e58-11e6-8a84-bae500000069",
          "type": "state",
          "mediaType": "application/json"
        }
      },
      "organizationAccount": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e/accounts/3a30e844-016f-11e6-9464-e4de00000068",
          "type": "account",
          "mediaType": "application/json"
        }
      },
      "productionRows": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026/productionRows",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
          "type": "processingorderproductionrow",
          "mediaType": "application/json",
          "size": 1,
          "limit": 1000,
          "offset": 0
        }
      }
    }
  ]
}
```

### Создать Заказ на производство 
Запрос на создание нового Заказа на производство.
Обязательные для создания поля:

+ **organization** - Ссылка на ваше юрлицо в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

> Пример создания нового Заказа с телом запроса, содержащим только необходимые поля.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingorder"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "organization": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
                "type": "organization",
                "mediaType": "application/json"
              }
            }
          }
'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorder",
    "mediaType": "application/json"
  },
  "id": "c49e83b3-01af-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
  "updated": "2016-04-14 13:08:58",
  "name": "000034",
  "externalCode": "DAD9peGij6sDNii49Dkam2",
  "created": "2007-02-07 17:16:41",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "moment": "2016-04-19 13:50:24",
  "applicable": false,
  "store": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "productStore": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "state": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata/states/fb56c504-2e58-11e6-8a84-bae500000069",
      "type": "state",
      "mediaType": "application/json"
    }
  },
  "organizationAccount": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e/accounts/3a30e844-016f-11e6-9464-e4de00000068",
      "type": "account",
      "mediaType": "application/json"
    }
  },
  "productionRows": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026/positions",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
      "type": "processingorderposition",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  }
}

```

### Удалить Заказ на производство

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|
 
> Запрос на удаление Заказа на производство с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление Заказа на производство.


### Заказ на производство

### Получить Заказ на производство

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: c49e83b3-01af-11e6-9464-e4de00000026* id Заказа на производство.|
 
> Запрос на получение отдельного Заказа на производство с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorder",
    "mediaType": "application/json"
  },
  "id": "c49e83b3-01af-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
  "updated": "2016-04-14 13:08:58",
  "name": "000034",
  "externalCode": "DAD9peGij6sDNii49Dkam2",
  "created": "2007-02-07 17:16:41",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "moment": "2016-04-19 13:50:24",
  "applicable": false,
  "store": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "productStore": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "state": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata/states/fb56c504-2e58-11e6-8a84-bae500000069",
      "type": "state",
      "mediaType": "application/json"
    }
  },
  "organizationAccount": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e/accounts/3a30e844-016f-11e6-9464-e4de00000068",
      "type": "account",
      "mediaType": "application/json"
    }
  },
  "productionRows": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026/productionRows",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
      "type": "processingorderproductionrow",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  }
}

```

### Изменить Заказ на производство 
Запрос на обновление Заказа на производство с указанным id.
В теле запроса можно указать только те поля, которые необходимо изменить у Заказа на производство, кроме тех, что
помечены `Только для чтения` в описании [атрибутов Заказа на производство](../documents/#dokumenty-zakaz-na-proizwodstwo).
При обновлении поля **organization** нужно также обновить поле **organizationAccount**, иначе произойдет ошибка.

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: c49e83b3-01af-11e6-9464-e4de00000026* id Заказа на производство.|

> Пример запроса на обновление отдельного Заказа на производство.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "000034",
            "quantity": 5,
            "processingPlan": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
                "type": "processingplan",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorder",
    "mediaType": "application/json"
  },
  "id": "c49e83b3-01af-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
  "updated": "2016-04-14 13:08:58",
  "name": "000034",
  "externalCode": "DAD9peGij6sDNii49Dkam2",
  "created": "2007-02-07 17:16:41",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "moment": "2016-04-19 13:50:24",
  "applicable": false,
  "store": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "productStore": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/28b74fd3-9e33-11e2-4670-001b21d91495",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=28b74fd3-9e33-11e2-4670-001b21d91495"
    }
  },
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "state": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata/states/fb56c504-2e58-11e6-8a84-bae500000069",
      "type": "state",
      "mediaType": "application/json"
    }
  },
  "organizationAccount": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e/accounts/3a30e844-016f-11e6-9464-e4de00000068",
      "type": "account",
      "mediaType": "application/json"
    }
  },
  "productionRows": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026/productionRows",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
      "type": "processingorderproductionrow",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  }
}
```

> Пример запроса на обновление Заказа на производство с позициями в теле запроса.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "positions": [
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/34efe2ee-015e-11e6-9464-e4de0000006b/positions/34f6344f-015e-11e6-9464-e4de0000006c",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
                  "type": "processingorderposition",
                  "mediaType": "application/json"
                },
                "id": "34f6344f-015e-11e6-9464-e4de0000006c",
                "quantity": 10,
                "assortment": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/8b382799-f7d2-11e5-8a84-bae5000003a5",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/34efe2ee-015e-11e6-9464-e4de0000006b/positions/34f6344f-015e-11e6-9464-e4de0000007c",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
                  "type": "processingorderposition",
                  "mediaType": "application/json"
                },
                "id": "34f6344f-015e-11e6-9464-e4de0000007c",
                "quantity": 20,
                "assortment": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/be903062-f504-11e5-8a84-bae50000019a",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/34efe2ee-015e-11e6-9464-e4de0000006b/positions/34f6344f-015e-11e6-9464-e4de0000008c",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
                  "type": "processingorderposition",
                  "mediaType": "application/json"
                },
                "id": "34f6344f-015e-11e6-9464-e4de0000008c",
                "quantity": 30,
                "assortment": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/c02e3a5c-007e-11e6-9464-e4de00000006",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                }
              }
            ]
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorder",
    "mediaType": "application/json"
  },
  "id": "c49e83b3-01af-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
  "updated": "2016-04-14 13:08:58",
  "name": "000034",
  "externalCode": "DAD9peGij6sDNii49Dkam2",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "moment": "2016-04-19 13:50:24",
  "applicable": false,
  "sum": 0,
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "state": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata/states/fb56c504-2e58-11e6-8a84-bae500000069",
      "type": "state",
      "mediaType": "application/json"
    }
  },
  "organizationAccount": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e/accounts/3a30e844-016f-11e6-9464-e4de00000068",
      "type": "account",
      "mediaType": "application/json"
    }
  },
  "created": "2007-02-07 17:16:41",
  "positions": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/c49e83b3-01af-11e6-9464-e4de00000026/positions",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
      "type": "processingorderposition",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  },
  "quantity": 5,
  "processingPlan": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
      "type": "processingplan",
      "mediaType": "application/json"
    }
  }
}
```

### Позиции Заказа на производство 
Отдельный ресурс для управления позициями Заказа на производство. С его помощью вы можете управлять позициями большого документа, количество строк в котором превышает лимит на количество строк, сохраняемых вместе с документом. Этот лимит равен 1000. Более подробно о лимитах на количество строк документа и работе с большими документами можно прочитать [тут](../#mojsklad-json-api-obschie-swedeniq-rabota-s-poziciqmi-dokumentow).

### Получить позиции Заказа на производство 
Запрос на получение списка всех позиций данного Заказа на производство.


| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные о выдаче,
**context** | [Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye) | Метаданные о сотруднике, выполнившем запрос.
**rows** |Array(Object)|Массив JSON объектов, представляющих собой позиции Заказа на производство.

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|
|**limit** |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|**offset** |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить позиции Заказа на производство

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка позиций отдельного Заказа на производство.

```json
{
  "context": {
    "employee": {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/context/employee",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
        "type": "employee",
        "mediaType": "application/json"
      }
    }
  },
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions",
    "type": "processingorderposition",
    "mediaType": "application/json",
    "size": 1,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/productionRows/c7218ccd-afcc-11e6-5bed-427b00000069",
        "type": "processingorderproductionrow",
        "mediaType": "application/json"
      },
      "id": "c7218ccd-afcc-11e6-5bed-427b00000069",
      "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
      "processingPlan": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
          "type": "processingplan",
          "mediaType": "application/json"
        }
      },
      "volume": 1,
      "costDistribution": "price",
      "products": [{
        "id": "2aee5718-2b9b-4cbf-9cda-e89487743d4e",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=e64d0a86-2a99-11e9-ac12-000c00000041"
          }
        },
        "quantity": 123,
        "processingPlanQuantity": 12,
        "reserve": 0
      }],
      "stages": [{
        "id": "d4719515-c349-4a91-8ce5-0f700f3e96ac",
        "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
        "name": "заготовка материалов",
        "personified": true,
        "cost": 1223,
        "salary": 20,
        "final": true,
        "materials": [{
          "id": "6dc8337d-7817-474e-a519-07232c8aeea2",
          "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=e64d0a86-2a99-11e9-ac12-000c00000041"
          },
          "reserve": 2,
          "quantity": 2,
          "processingPlanQuantity": 12
        }]
      }]
    }
  ]
}
```

### Ряд продукции Заказа на производство 
Отдельный ряд продукции Заказа с указанным id ряда.

### Получить позицию Заказа на производство

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|
|**positionID** |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id ряда продукции Заказа на производство.|
 
> Запрос на получение отдельной позиции Заказа с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/productionRows/34f6344f-015e-11e6-9464-e4de0000006c"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельной позиции Заказа на производство.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/productionRows/c7218ccd-afcc-11e6-5bed-427b00000069",
    "type": "processingorderproductionrow",
    "mediaType": "application/json"
  },
  "id": "c7218ccd-afcc-11e6-5bed-427b00000069",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "processingPlan": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
      "type": "processingplan",
      "mediaType": "application/json"
    }
  },
  "volume": 1,
  "costDistribution": "price",
  "products": [{
    "id": "2aee5718-2b9b-4cbf-9cda-e89487743d4e",
    "assortment": {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
        "type": "product",
        "mediaType": "application/json",
        "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=e64d0a86-2a99-11e9-ac12-000c00000041"
      }
    },
    "quantity": 123,
    "processingPlanQuantity": 12,
    "reserve": 0
  }],
  "stages": [{
    "id": "d4719515-c349-4a91-8ce5-0f700f3e96ac",
    "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
    "name": "заготовка материалов",
    "personified": true,
    "cost": 1223,
    "salary": 20,
    "final": true,
    "materials": [{
      "id": "6dc8337d-7817-474e-a519-07232c8aeea2",
      "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
        "type": "product",
        "mediaType": "application/json",
        "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=e64d0a86-2a99-11e9-ac12-000c00000041"
      },
      "reserve": 2,
      "quantity": 2,
      "processingPlanQuantity": 12
    }]
  }]
}

```

### Добавить позицию Заказа на производство
Запрос на добавление отдельного ряда продукции для Заказа.

**Параметры**

|Параметр   |Описание   |
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|

> Пример запроса на создание отдельного ряда продукции в Заказе на производство.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/productionRows/"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "volume": 12,
            "processingPlan": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
                "type": "processingplan",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного ряда продукции Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions/34f6344f-015e-11e6-9464-e4de0000006c",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorderposition",
    "mediaType": "application/json"
  },
  "id": "34f6344f-015e-11e6-9464-e4de0000006c",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "quantity": 111,
  "assortment": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/eeef177f-f648-11e5-8a84-bae50000007a",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=3b1e1f15-2842-11e9-ac12-000c0000002f"
    }
  },
  "reserve": 0
}
```

### Изменить позицию Заказа на производство 
Запрос на обновление отдельной позиции Заказа. Для обновления позиции нет каких-либо
 обязательных для указания в теле запроса полей. Только те, что вы желаете обновить.

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|
|**positionID** |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id позиции Заказа на производство.|

> Пример запроса на обновление отдельной позиции в Заказе на производство.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions/34f6344f-015e-11e6-9464-e4de0000006c"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions/34f6344f-015e-11e6-9464-e4de0000006c",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
              "type": "processingorderposition",
              "mediaType": "application/json"
            },
            "id": "34f6344f-015e-11e6-9464-e4de0000006c",
            "quantity": 111,
            "assortment": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/eeef177f-f648-11e5-8a84-bae50000007a",
                "type": "product",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленной позиции Заказа на производство.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions/34f6344f-015e-11e6-9464-e4de0000006c",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
    "type": "processingorderposition",
    "mediaType": "application/json"
  },
  "id": "34f6344f-015e-11e6-9464-e4de0000006c",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "quantity": 111,
  "assortment": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/eeef177f-f648-11e5-8a84-bae50000007a",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#good/edit?id=3b1e1f15-2842-11e9-ac12-000c0000002f"
    }
  },
  "reserve": 0
}
```

### Удалить позицию

**Параметры**

|Параметр   |Описание   | 
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Заказа на производство.|
|**positionID** |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id позиции Заказа на производство.|
 
> Запрос на удаление позиции Заказа на производство с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/processingorder/7944ef04-f831-11e5-7a69-971500188b19/positions/34f6344f-015e-11e6-9464-e4de0000006c"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление позиции Заказа на производство.
