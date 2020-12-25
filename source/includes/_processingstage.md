## Этап производства
### Этапы
Средствами JSON API можно создавать и обновлять сведения о Этапах, запрашивать списки Этапов и сведения по отдельным Этапам. Кодом сущности для Этапа в составе JSON API является ключевое слово **processingstage**.

#### Атрибуты сущности
| Название  | Тип | Описание                    | Свойство поля в запросе | Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**meta**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Этапа|&mdash;|да
|**id**                |UUID|ID этапа|Только для чтения|да
|**accountId**         |UUID|ID учетной записи|Только для чтения|да
|**owner**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные владельца (Сотрудника)|&mdash ;|да
|**shared**         |Boolean|Общий доступ|&mdash;|да
|**group**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные отдела сотрудника|&mdash;|да
|**updated**         |DateTime|Момент последнего обновления сущности|Только для чтения|да
|**name**         |String(255)|Наименование Этапа|Необходимое при создании|да
|**description**        |String(4096)|Описание Этапа|&mdash;|нет
|**externalCode**         |String(255)|Внешний код Этапа|&mdash;|да
|**archived**        |Boolean|Добавлен ли этап в архив|&mdash;|да


### Получить Этапы
Запрос на получение списка всех этапов на данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные о выдаче,
**context** | [Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye) | Метаданные о сотруднике, выполнившем запрос.
**rows** |Array(Object)| Массив JSON объектов, представляющих собой этапы.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|**limit** |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|**offset** |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить этапы

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingstage"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка этапов.

```json
{
  "context": {
    "employee": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/employee",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
        "type": "employee",
        "mediaType": "application/json"
      }
    }
  },
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
    "type": "processingstage",
    "mediaType": "application/json",
    "size": 2,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/51f263f9-0307-11e6-9464-e4de0000007c",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
        "type": "processingstage",
        "mediaType": "application/json"
      },
      "id": "51f263f9-0307-11e6-9464-e4de0000007c",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
      "updated": "2016-04-15 15:41:05",
      "name": "Распил",
      "description": "Этап распила дерева на доски",
      "externalCode": "HZV7dGc8iAnf0aNjrvQvN0",
      "archived": false,
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/8477d916-0aef-11e6-9464-e4de00000103",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
        "type": "processingstage",
        "mediaType": "application/json"
      },
      "id": "8477d916-0aef-11e6-9464-e4de00000103",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
      "updated": "2016-04-25 17:10:51",
      "name": "Покраска",
      "description": "Этап покраски и лакировки досок",
      "externalCode": "lv7MmPK4jvaqq-nA3g3NL2",
      "archived": false
    }
  ]
}
```

### Создать Этап
Запрос на создание нового этапа. Единственным необходимым полем в теле запроса
для создания этапа является **name**.

> Пример запроса на создание нового этапа.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingstage"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Распил",
            "description": "Распил дерева на доски",
            "externalCode": "814fhsafiwb124"
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Этапа.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/2c013eeb-0af0-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
    "type": "processingstage",
    "mediaType": "application/json"
  },
  "id": "2c013eeb-0af0-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
  "updated": "2016-04-25 17:15:32",
  "name": "Распил",
  "description": "Распил дерева на доски",
  "externalCode": "814fhsafiwb124",
  "archived": false
}
```

### Массовое создание и обновление Этапов
[Массовое создание и обновление](../#mojsklad-json-api-obschie-swedeniq-sozdanie-i-obnowlenie-neskol-kih-ob-ektow) этапов.
В теле запроса нужно передать массив, содержащий JSON представления этапов, которые вы хотите создать или обновить.
Обновляемые этапы должны содержать идентификатор в виде метаданных.

> Пример создания и обновления нескольких этапов

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingstage"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '[
            {
              "name": "Новый этап",
              "description": "Новый этап",
              "externalCode": "814fhsafiwb124"
            },
            {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/76e88dff-3f9b-11e6-8a84-bae50000009b",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
                "type": "processingstage",
                "mediaType": "application/json"
              },
              "description": "Обновление Этапа",
              "externalCode": "dfDGFSG44"
            }
          ]'  
```

> Response 200 (application/json)
Успешный запрос. Результат - массив JSON представлений созданных и обновленных этапов.

```json
[
  {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/2c013eeb-0af0-11e6-9464-e4de00000026",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
      "type": "processingstage",
      "mediaType": "application/json"
    },
    "id": "2c013eeb-0af0-11e6-9464-e4de00000026",
    "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
    "updated": "2016-04-25 17:15:32",
    "name": "Новый этап",
    "description": "Новый этап",
    "externalCode": "814fhsafiwb124",
    "archived": false
  },
  {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/76e88dff-3f9b-11e6-8a84-bae50000009b",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
      "type": "processingstage",
      "mediaType": "application/json"
    },
    "id": "76e88dff-3f9b-11e6-8a84-bae50000009b",
    "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
    "updated": "2016-04-25 17:17:21",
    "name": "Важный этап",
    "description": "Обновление Этапа",
    "externalCode": "dfDGFSG44",
    "archived": false
  }
]
```

### Удалить Этап

**Параметры**

|Параметр   |Описание   |
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id этапа.|

> Запрос на удаление этапа с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление этапа.

### Массовое удаление этапов

В теле запроса нужно передать массив, содержащий JSON метаданных этапов, которые вы хотите удалить.


> Запрос на массовое удаление этапов.

```shell
curl -X POST
  "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/delete"
  -H "Authorization: Basic <Credentials>"
  -H "Content-Type: application/json"
  -d '[
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/7944ef04-f831-11e5-7a69-971500188b1",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
            "type": "processingstage",
            "mediaType": "application/json"
        },
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/7944ef04-f831-11e5-7a69-971500188b2",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
            "type": "processingstage",
            "mediaType": "application/json"
        }
      ]'
```        

> Успешный запрос. Результат - JSON информация об удалении этапов.

```json
[
  {
    "info":"Сущность 'processingstage' с UUID: 7944ef04-f831-11e5-7a69-971500188b1 успешно удалена"
  },
  {
    "info":"Сущность 'processingstage' с UUID: 7944ef04-f831-11e5-7a69-971500188b2 успешно удалена"
  }
]
```

### Этап

**Параметры**

|Параметр   |Описание   |
|:&mdash;|:&mdash;|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id этапа.|

### Получить этап
> Запрос на получение отдельного Этапа с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление этапа.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/51f263f9-0307-11e6-9464-e4de0000007c",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
    "type": "processingstage",
    "mediaType": "application/json"
  },
  "id": "51f263f9-0307-11e6-9464-e4de0000007c",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
  "updated": "2016-04-15 15:41:05",
  "name": "Распил",
  "description": "Этап распила древесины на доски",
  "externalCode": "HZV7dGc8iAnf0aNjrvQvN0",
  "archived": false
  ]
}
```

### Изменить Этап
Запрос на обновление существующего этапа с указанным id.

**Параметры**

|Параметр   |Описание   |
|:&mdash;|:&mdash;|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id этапа.|

> Пример запроса на обновление существующего Этапа.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/7944ef04-f831-11e5-7a69-971500188b19"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Распил",
            "description": "Этап распила древесины на доски",
            "externalCode": "cas12rgs"
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Этапа.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/2c013eeb-0af0-11e6-9464-e4de00000026",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/processingstage/metadata",
    "type": "processingstage",
    "mediaType": "application/json"
  },
  "id": "2c013eeb-0af0-11e6-9464-e4de00000026",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
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
  "updated": "2016-04-25 17:17:21",
  "name": "Распил",
  "description": "Этап распила древесины на доски",
  "externalCode": "cas12rgs",
  "archived": false
}
```
