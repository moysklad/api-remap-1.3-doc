## Техкарта
Средствами JSON API можно создавать и обновлять сведения о Техкартах, запрашивать списки Техкарт и сведения по отдельным Техкартам. Позициями Техкарт можно управлять как в составе отдельной Техкарты, так и отдельно - с помощью специальных ресурсов для управления материалами и продуктами Техкарты. Кодом сущности для Техкарты в составе JSON API является ключевое слово **processingplan**. Больше о Техкартах и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки по
[этой ссылке](https://support.moysklad.ru/hc/ru/articles/203325613-%D0%A1%D0%B1%D0%BE%D1%80%D0%BE%D1%87%D0%BD%D1%8B%D0%B5-%D0%B8-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8).
### Техкарты 
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
|**processingProcess**         |([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Метаданные процесса Техкарты|Необходимое при создании|да
|**materials**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных материалов Техкарты|Необходимое при создании|да
|**products**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных готовых продуктов Техкарты|Необходимое при создании|да
|**costDistribution**         |String|Тип распределения себестоимости, может принимать значения "price" или "percent"|По умолчанию создается с типом распределения по ценам продаж|да

#### Материалы Техкарты
Материалы Техкарты — это список товаров, используемых для производства готовых продуктов.
Объект материала Техкарты содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Материала|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**product**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара позиции|&mdash;|нет
|**processingStage**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные этапа, на котором произойдет списание материала|&mdash;|нет
|**quantity**               |Int|Количество товаров данного вида в позиции|&mdash;|да

#### Продукты Техкарты
Продукты Техкарты — это список товаров, получаемых при производстве.
Объект продукта Техкарты содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Продукта|Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**product**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара позиции|&mdash;|нет
|**quantity**               |Int|Количество товаров данного вида в позиции|&mdash;|да
|**costShare**               |Int|Процентное распределение себестоимости в случае если выбран тип распределений себестоимости в процентах|&mdash;|да

#### Этапы Техкарты
Этапы Техкарты — это список этапов Техкарты, из которых состоит связанный производственный процесс. Материалы привязываются к этапам
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

### Техкарта

### Получить Техкарту

**Параметры**

| Параметр | Описание |
| -------- |:---|
| **id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Техкарты.|

> Запрос на получение отдельной Техкарты с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingplan/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Техкарты.

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
  "processingProcess": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/0da78cd1-91f2-11e6-5bed-456b0000009a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/metadata",
      "type": "processingprocess",
      "mediaType": "application/json"
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

### Создать Техкарту
Запрос на создание новой Техкарты.
Обязательные для создания поля:

+ **name** - Наименование Тех. карты
+ **processingProcess** - Список материалов Тех. карты в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **products** - Список готовых продуктов Тех. карты в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

> Пример создания новой Тех.карты

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingplan"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Example",
            "cost": 1000,
            "processingProcess": {
              "meta": {
                  "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/0da78cd1-91f2-11e6-5bed-456b0000009a",
                   "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/metadata",
                   "type": "processingprocess",
                   "mediaType": "application/json"
               }
            },
            "materials": [
              {
                "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "processingStage": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingstage/f60079a5-36c6-4f6c-9b37-433e185f14df",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 1
              }
            ],
            "products": [
              {
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0da78cd1-91f2-11e6-5bed-427b0000009a",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 1
              },
              {
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0da78cd1-91f2-11e6-5bed-427b0000009a",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 1
              }
            ]
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Техкарты.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
    "type": "processingplan",
    "mediaType": "application/json"
  },
  "id": "120a488b-b0bd-11e6-5bed-427b00000000",
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
  "processingProcess": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/0da78cd1-91f2-11e6-5bed-456b0000009a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/metadata",
      "type": "processingprocess",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-22 17:07:57",
  "name": "123sdf",
  "externalCode": "llZWq551h90XDJuYADvry0",
  "pathName": "",
  "cost": 1000,
  "costDistibution": "price",
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000/materials",
      "type": "processingplanmaterial",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000/products",
      "type": "processingplanresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```

> Пример создания новой Техкарты с процентным распределением себестоимости

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingplan"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Example",
            "cost": 1000,
            "processingProcess": {
              "meta": {
                  "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/0da78cd1-91f2-11e6-5bed-456b0000009a",
                   "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/metadata",
                   "type": "processingprocess",
                   "mediaType": "application/json"
               }
            },
            "costDistribution": "percent",
            "materials": [
              {
                "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "processingStage": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingstage/f60079a5-36c6-4f6c-9b37-433e185f14df",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 1
              }
            ],
            "products": [
              {
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0da78cd1-91f2-11e6-5bed-427b0000009a",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "costShare": 40
                "quantity": 1
              },
              {
                "product": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0da78cd1-91f2-11e6-5bed-427b0000009a",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "costShare": 60
                "quantity": 1
              }
            ]
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Тех. карты.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
    "type": "processingplan",
    "mediaType": "application/json"
  },
  "id": "120a488b-b0bd-11e6-5bed-427b00000000",
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
  "processingProcess": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/0da78cd1-91f2-11e6-5bed-456b0000009a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingprocess/metadata",
      "type": "processingprocess",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-22 17:07:57",
  "name": "123sdf",
  "externalCode": "llZWq551h90XDJuYADvry0",
  "pathName": "",
  "cost": 1000,
  "costDistibution": "percent",
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000/materials",
      "type": "processingplanmaterial",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/120a488b-b0bd-11e6-5bed-427b00000000/products",
      "type": "processingplanresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```
