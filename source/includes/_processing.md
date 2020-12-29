## Техоперация
Средствами JSON API можно создавать и обновлять сведения о Техоперациях, запрашивать списки Техопераций и сведения по отдельным Техоперациям. Позициями Техопераций можно управлять как в составе отдельной Техоперации, так и отдельно - с помощью специальных ресурсов для управления материалами и продуктами Техоперации. Кодом сущности для Техоперации в составе JSON API является ключевое слово **processing**. Больше о Техоперациях и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки по
[этой ссылке](https://support.moysklad.ru/hc/ru/articles/203325613-%D0%A1%D0%B1%D0%BE%D1%80%D0%BE%D1%87%D0%BD%D1%8B%D0%B5-%D0%B8-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8).
### Техоперации 
#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**meta**               |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Тех. операции |Только для чтения|да
|**id**                 |UUID|ID Тех. операции |Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**syncId**             |UUID|ID синхронизации. После заполнения недоступен для изменения|Только для чтения|нет
|**updated**            |DateTime|Момент последнего обновления Тех. операции |Только для чтения|да
|**deleted**            |DateTime|Момент последнего удаления Тех. операции |Только для чтения|нет
|**name**               |String(255)|Наименование Тех. операции |Необходимое при создании|да
|**description**        |String(4096)|Комментарий Тех. операции |&mdash;|нет
|**externalCode**       |String(255)|Внешний код Тех. операции |Только для чтения| да
|**moment**             |DateTime|Дата смены|Только для чтения|да
|**applicable**         |Boolean|Отметка о проведении|&mdash;|да
|**project**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные проекта|&mdash;|нет
|**owner**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Владелец (Сотрудник)|&mdash;|да
|**shared**             |Boolean|Общий доступ|Только для чтения|да
|**group**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Отдел сотрудника|&mdash;|да
|**organization**       |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные юрлица|Необходимое при создании|да
|**state**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные статуса Тех. операции |&mdash;|нет
|**organizationAccount**|[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные счета юрлица|&mdash;|нет
|**attributes**         |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Коллекция метаданных доп. полей. [Поля при expand'е](../documents/#dokumenty-teh-operaciq-teh-operacii-atributy-suschnosti-polq-pri-expand-39-e-dop-polej) |&mdash;|нет
|**files**              |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Массив метаданных [Файлов](../dictionaries/#suschnosti-fajly) (Максимальное количество файлов - 100)|&mdash;|да
|**created**            |DateTime|Дата создания|Только для чтения|да
|**volume**             |Int|Объем производства|Необходимое при создании|да
|**processingSum**              |Int|Затраты на производство|Необходимое при создании|да
| **materials**          |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Список Метаданных материалов Тех. операции|Необходимое при создании|да
| **products**          |Array([Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye))|Список Метаданных готовых продуктов Тех. операции|Необходимое при создании|да
| **productsStore**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада для продукции|Необходимое при создании|да
| **materialsStore**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада для материалов|Необходимое при создании|да
| **processingPlan**           |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Техкарты|Необходимое при создании если создается на основе Техкарты|нет
|**costDistribution**          |String|Тип распределения себестоимости для ряда продукции по техкарте. Может принимать 2 значения: "price" - распределение по ценам продаж или "percent" - процентное распределение.|&mdash;|да

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
|**processingOrder**               |Ссылка на заказ на производство в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

#### Материалы Техоперации
Материалы Техоперации - это список товаров/модификаций/серий, используемых для производства готовых продуктов согласно тех. карте.
Объект материала Техоперации содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Тех. операции |Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**assortment**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара/серии/модификации, которую представляет собой позиция|&mdash;|да
|**quantity**          |Int|Количество товаров данного вида в позиции|&mdash;|да

#### Продукты Техоперации
Продукты Техоперации - это список товаров/модификаций/серий, получаемых при производстве согласно тех. карте.
Объект продукта Техоперации содержит следующие поля:

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**id**                 |UUID|ID Тех. операции |Только для чтения|да
|**accountId**          |UUID| ID учетной записи|Только для чтения|да
|**assortment**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные товара/серии/модификации, которую представляет собой позиция|&mdash;|да
|**quantity**          |Int|Количество товаров данного вида в позиции|&mdash;|да

С материалами и продуктами можно работать с помощью [специальных ресурсов для управления позициями Техоперации](../documents/#dokumenty-teh-operaciq-izmenit-teh-operaciu-materialy-teh-operacii),
а также в составе отдельной Техоперации. При работе в составе отдельной Техоперации,
вы можете отправлять запросы на создание отдельной Техоперации с включенными в тело запроса
массивами материалов и продуктов Техоперации.
Также, при работе в составе отдельной Техоперации, можно отправлять запросы на обновление списка материалов и продуктов
с включенными в тело запроса массивами материалов и продуктов Техоперации.


### Получить список Техопераций 
Запрос всех Техопераций на данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные о выдаче,
**context** | [Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye) | Метаданные о сотруднике, выполнившем запрос.
**rows** |Array(Object)|Массив JSON объектов, представляющих собой Техоперации.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|**limit** |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|**offset** |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|
|**search** |  `string` (optional) *Example: 0001* Фильтр документов по указанной поисковой строке.

> Получить список Техопераций

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processing"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка Техопераций.

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
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
    "type": "processing",
    "mediaType": "application/json",
    "size": 1,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
        "type": "processing",
        "mediaType": "application/json"
      },
      "id": "493ddf6b-aff9-11e6-5bed-427b00000076",
      "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
      "owner": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": false,
      "group": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "updated": "2016-11-21 17:46:29.000",
      "name": "я1",
      "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
      "moment": "2016-11-21 17:46:00.000",
      "applicable": true,
      "project": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
          "type": "project",
          "mediaType": "application/json"
        }
      },
      "organization": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
          "type": "organization",
          "mediaType": "application/json"
        }
      },
      "processingSum": 10000,
      "volume": 1,
      "processingPlan": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
          "type": "processingplan",
          "mediaType": "application/json"
        }
      },
      "productsStore": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
          "type": "store",
          "mediaType": "application/json"
        }
      },
      "materialsStore": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
          "type": "store",
          "mediaType": "application/json"
        }
      },
      "processingOrder": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/c7201428-afcc-11e6-5bed-427b00000068",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
          "type": "processingorder",
          "mediaType": "application/json"
        }
      },
      "products": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/products",
          "type": "processingpositionresult",
          "mediaType": "application/json",
          "size": 2,
          "limit": 1000,
          "offset": 0
        }
      },
      "materials": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/materials",
          "type": "processingpositionmaterial",
          "mediaType": "application/json",
          "size": 2,
          "limit": 1000,
          "offset": 0
        }
      },
      "costDistribution": "price"
    }
  ]
}
```

### Создать Техоперацию
Запрос на создание новой Техоперации.
Обязательные для создания поля:

+ **organization** - Ссылка на ваше юрлицо в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **processingSum** - Затраты на производство
+ **productsStore** - Ссылка на склад для продукции в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **materialsStore** - Ссылка на склад для материалов в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

> Пример создания новой Техоперации с телом запроса, содержащим только необходимые поля.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processing"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "organization": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
                "type": "organization",
                "mediaType": "application/json"
              }
            },
            "processingSum": 10000,
            "productsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            },
            "materialsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Тех. операции.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
    "type": "processing",
    "mediaType": "application/json"
  },
  "id": "493ddf6b-aff9-11e6-5bed-427b00000076",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-21 17:46:29",
  "name": "00001",
  "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
  "moment": "2016-11-21 17:46:00",
  "applicable": true,
  "organization": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "processingSum": 10000,
  "volume": 1,
  "productsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "materialsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/products",
      "type": "processingpositionresult",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/materials",
      "type": "processingpositionmaterial",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  }
}
```

> Пример создания новой Техоперации.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processing"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "owner": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
                "type": "employee",
                "mediaType": "application/json"
              }
            },
            "shared": false,
            "group": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
                "type": "group",
                "mediaType": "application/json"
              }
            },
            "updated": "2016-11-21 17:46:29",
            "name": "Это технологическая операция",
            "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
            "moment": "2016-11-21 17:46:00",
            "applicable": true,
            "costDistribution": "percent",
            "project": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
                "type": "project",
                "mediaType": "application/json"
              }
            },
            "organization": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
                "type": "organization",
                "mediaType": "application/json"
              }
            },
            "processingSum": 10000,
            "productsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            },
            "materialsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            },
            "processingOrder": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/c7201428-afcc-11e6-5bed-427b00000068",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
                "type": "processingorder",
                "mediaType": "application/json"
              }
            },
            "products": {
              "meta": {
                "type": "processingpositionresult",
                "mediaType": "application/json",
                "size": 2,
                "limit": 1000,
                "offset": 0
              },
              "rows": [
                {
                  "quantity": 3,
                  "costShare": 40,
                  "assortment": {
                    "meta": {
                      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/160ff7bb-acdc-11e6-5bed-427b0000008c",
                      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                      "type": "product",
                      "mediaType": "application/json"
                    }
                  }
                },
                {
                  "quantity": 2,
                  "costShare": 60
                  "assortment": {
                    "meta": {
                      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/18fce7bf-acdc-11e6-5bed-427b00000092",
                      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                      "type": "product",
                      "mediaType": "application/json"
                    }
                  }
                }
              ]
            },
            "materials": {
              "meta": {
                "type": "processingpositionmaterial",
                "mediaType": "application/json",
                "size": 2,
                "limit": 1000,
                "offset": 0
              },
              "rows": [
                {
                  "quantity": 4,
                  "assortment": {
                    "meta": {
                      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/0de151c1-acdc-11e6-5bed-427b00000080",
                      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                      "type": "product",
                      "mediaType": "application/json"
                    }
                  }
                },
                {
                  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
                  "quantity": 1,
                  "assortment": {
                    "meta": {
                      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/1267a23f-acdc-11e6-5bed-427b00000086",
                      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                      "type": "product",
                      "mediaType": "application/json"
                    }
                  }
                }
              ]
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Техоперации.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
    "type": "processing",
    "mediaType": "application/json"
  },
  "id": "493ddf6b-aff9-11e6-5bed-427b00000076",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-21 17:46:29",
  "name": "Это технологическая операция",
  "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
  "moment": "2016-11-21 17:46:00",
  "applicable": true,
  "project": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
      "type": "project",
      "mediaType": "application/json"
    }
  },
  "organization": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "processingSum": 10000,
  "volume": 1,
  "productsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "materialsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "processingOrder": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/c7201428-afcc-11e6-5bed-427b00000068",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingorder/metadata",
      "type": "processingorder",
      "mediaType": "application/json"
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/products",
      "type": "processingpositionresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  },
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/materials",
      "type": "processingpositionmaterial",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```

> Пример создания новой Техоперации на основании Техкарты.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processing"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "owner": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
                "type": "employee",
                "mediaType": "application/json"
              }
            },
            "shared": false,
            "group": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
                "type": "group",
                "mediaType": "application/json"
              }
            },
            "updated": "2016-11-21 17:46:29",
            "name": "Это технологическая операция",
            "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
            "moment": "2016-11-21 17:46:00",
            "applicable": true,
            "project": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
                "type": "project",
                "mediaType": "application/json"
              }
            },
            "organization": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
                "type": "organization",
                "mediaType": "application/json"
              }
            },
            "processingSum": 10000,
            "volume": 2,
            "processingPlan": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
                "type": "processingplan",
                "mediaType": "application/json"
              }
            },
            "productsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            },
            "materialsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Техоперации.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
    "type": "processing",
    "mediaType": "application/json"
  },
  "id": "493ddf6b-aff9-11e6-5bed-427b00000076",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-21 17:46:29",
  "name": "Это технологическая операция",
  "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
  "moment": "2016-11-21 17:46:00",
  "applicable": true,
  "project": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
      "type": "project",
      "mediaType": "application/json"
    }
  },
  "organization": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "processingSum": 10000,
  "volume": 2,
  "processingPlan": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
      "type": "processingplan",
      "mediaType": "application/json"
    }
  },
  "productsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "materialsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/products",
      "type": "processingpositionresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  },
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/materials",
      "type": "processingpositionmaterial",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```


> Пример создания новой Техоперации на основании Заказа на производство.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processing"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "owner": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
                "type": "employee",
                "mediaType": "application/json"
              }
            },
            "shared": false,
            "group": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
                "type": "group",
                "mediaType": "application/json"
              }
            },
            "updated": "2016-11-21 17:46:29",
            "name": "Это технологическая операция",
            "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
            "moment": "2016-11-21 17:46:00",
            "applicable": true,
            "project": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
                "type": "project",
                "mediaType": "application/json"
              }
            },
            "organization": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
                "type": "organization",
                "mediaType": "application/json"
              }
            },
            "processingSum": 10000,
            "volume": 2,
            "processingPlan": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
                "type": "processingplan",
                "mediaType": "application/json"
              }
            },
            "productsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            },
            "materialsStore": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
              }
            }
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной Техоперации.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processing/metadata",
    "type": "processing",
    "mediaType": "application/json"
  },
  "id": "493ddf6b-aff9-11e6-5bed-427b00000076",
  "accountId": "d55cbfba-91f1-11e6-5bed-427b00000000",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/d5ad957e-91f1-11e6-5bed-427b0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/d55da707-91f1-11e6-5bed-427b00000001",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-11-21 17:46:29",
  "name": "Это технологическая операция",
  "externalCode": "JhQJY8u1isyuqHyn7B6Wx3",
  "moment": "2016-11-21 17:46:00",
  "applicable": true,
  "project": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/project/7f3a7d7a-97a1-11e6-5bed-427b0000009c",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/project/metadata",
      "type": "project",
      "mediaType": "application/json"
    }
  },
  "organization": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/organization/a1331985-a1c8-11e6-5bed-427b00000084",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "processingSum": 10000,
  "volume": 2,
  "processingPlan": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/c38e50b0-acdc-11e6-5bed-427b0000009e",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/processingplan/metadata",
      "type": "processingplan",
      "mediaType": "application/json"
    }
  },
  "productsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/c61ce912-a747-11e6-5bed-427b000000a8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "materialsStore": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/store/d5e311c0-91f1-11e6-5bed-427b00000053",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "products": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/products",
      "type": "processingpositionresult",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  },
  "materials": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/processing/493ddf6b-aff9-11e6-5bed-427b00000076/materials",
      "type": "processingpositionmaterial",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```
