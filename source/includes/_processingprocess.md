## Процесс производства

### Процессы

Средствами JSON API можно создавать и обновлять сведения о Процессах производства, запрашивать списки Процессов и
сведения по отдельным Процессам. Кодом сущности для Процесса в составе JSON API является ключевое слово **
processingprocess**.

#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе | Обязательное при ответе|
| --------- |:----|:----------------------------|:----------------|:------------------------|
|**meta**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Процесса|&mdash;|да
|**id**                |UUID|ID процесса|Только для чтения|да
|**accountId**         |UUID|ID учетной записи|Только для чтения|да
|**
owner**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные владельца (Сотрудника)|&mdash ;|да
|**shared**         |Boolean|Общий доступ|&mdash;|да
|**group**         |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные отдела сотрудника|&mdash;|да
|**updated**         |DateTime|Момент последнего обновления сущности|Только для чтения|да
|**name**         |String(255)|Наименование Процесса|Необходимое при создании|да
|**description**        |String(4096)|Описание Процесса|&mdash;|нет
|**externalCode**         |String(255)|Внешний код Процесса|&mdash;|да
|**archived**        |Boolean|Добавлен ли Процесс в архив|&mdash;|да
|**processingStages**|Array(Object)|Массив этапов Процесса|Необходимо при создании|да

### Создать Процесс

Запрос на создание нового Процесса. Необходимыми полями в теле запроса для создания процесса являются **name**, **
processingStages**. Структура связей этапов processingStages должна сводиться к виду, при котором имеется 1 последний
этап, и все остальные этапы либо напрямую, либо через своих потомков с ним связаны и ему предшествующим. В случае если это
требование не соблюдается, то создание или изменение будет невозможно и сервис ответит ошибкой.

> Пример запроса на создание нового процесса.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/processingstage"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
   "name":"Сборка мебели",
   "processingStages":[
      {
         "processingStage":{
            "meta":{
               "href":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/56b3a47f-3a00-11eb-0a80-1702000002b0",
               "metadataHref":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
               "type":"processingstage",
               "mediaType":"application/json"
            }
         }
      },
      {
         "processingStage":{
            "meta":{
               "href":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/22b3a47f-3a00-11eb-0a80-1702000002b0",
               "metadataHref":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
               "type":"processingstage",
               "mediaType":"application/json"
            }
         },
         "previousStages":[
            {
               "meta":{
                  "href":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/56b3a47f-3a00-11eb-0a80-1702000002b0",
                  "metadataHref":"https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
                  "type":"processingstage",
                  "mediaType":"application/json"
               }
            }
         ]
      }
   ]
}
'  
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
  "processingStages": [
    {
      "id": "58e48338-7ae9-4706-b303-0fff1c0c528d",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
      "processingStage": {
        "meta": {
          "href": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/56b3a47f-3a00-11eb-0a80-1702000002b0",
          "metadataHref": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
          "type": "processingstage",
          "mediaType": "application/json"
        }
      }
    },
    {
      "id": "d46230c0-6b19-49ad-a34e-917be37bf87f",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
      "processingStage": {
        "meta": {
          "href": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/22b3a47f-3a00-11eb-0a80-1702000002b0",
          "metadataHref": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
          "type": "processingstage",
          "mediaType": "application/json"
        }
      },
      "previousStages": [
        {
          "meta": {
            "href": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/56b3a47f-3a00-11eb-0a80-1702000002b0",
            "metadataHref": "https://online-analytics-1.testms.lognex.ru/api/remap/1.3/entity/processingStage/metadata",
            "type": "processingstage",
            "mediaType": "application/json"
          }
        }
      ]
    }
  ],
  "updated": "2016-04-25 17:15:32",
  "name": "Сборка мебели",
  "description": "",
  "externalCode": "814fhsafiwb124",
  "archived": false
}
```
