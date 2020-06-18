## Файлы

### Работа с Файлами в рамках отдельных Операции, Номенклатуры или Контрагента
При создании и обновлении Операции, Номенклатуры или Контрагента можно указать поле files со списком элементов, имеющих следующие атрибуты:

+ **filename** - имя файла с расширением. Например - "doc.pdf"
+ **content** - файл, закодированный в формате Base64.

В таком случае, массив Файлов воспринимается как множество всех Файлов объекта и полностью заменяет (в случае запроса на обновление) все 
уже существующие Файлы в объекте. В случае запроса на обновление, все Файлы, которые существовали ранее в объекте будут удалены, 
а новые Файлы будут добавлены в список Файлов.
Если в запросе на обновление files будет содержать пустой массив элементов, то все Файлы у Операции, Номенклатуры или Контрагента будут удалены, т.к. 
сервер посчитает, что пользователь хочет обновить список Файлов Операции, Номенклатуры или Контрагента.

Лимит Файлов сохраняемых вместе с объектом равен 10, если вам нужно загрузить больше Файлов для одного объекта, нужно использовать способ описанный ниже. 


### Работа с Файлами Операции, Номенклатуры или Контрагента с помощью специальных ресурсов
Средствами JSON API можно создавать и обновлять сведения по Файлам для всех типов операций, товаров и контрагентов, запрашивать списки Файлов, 
а также сведения по отдельным Файлам. 

Операции, товары и контрагенты могут содержать множество одинаковых Файлов. Файлы считаются одинаковыми, если при добавлении Файлов 
у них совпадало `filename` и `content`. У одинаковых Файлов одинаковое значение параметра `id`. 
У объекта может быть не более 100 Файлов.

#### Атрибуты сущности
+ **meta** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) объекта
+ **title** - Название Файла
+ **filename** - Имя Файла
+ **size** - Размер Файла в байтах
+ **created** - Время загрузки Файла на сервер
+ **createdBy** - Ссылка на сотрудника, загрузившего Файл, в формате Метеданных
+ **download** - Ссылка на Файл в формате Метаданных
+ **miniature** - Ссылка на миниатюру изображения в формате Метаданных (поле передается только для Файлов изображений)
+ **tiny** - Ссылка на уменьшенное изображение в формате Метаданных (поле передается только для Файлов изображений)

### Получить список Файлов Операции, Номенклатуры или Контрагента
Запрос на получение всех Файлов Операции, Номенклатуры или Контрагента для данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

- **meta** [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о выдаче,
- **context** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой [Файлы](../dictionaries/#suschnosti-fajly).

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|type |  `string` (required) *Example: product* тип сущности, для которой запрашиваются Файлы.|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Товара c Файлами.|
|limit |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|offset |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить список Изображений для Товара

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files"
  -H "Authorization: Basic <Credentials>"
```

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
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files",
        "type": "files",
        "mediaType": "application/json",
        "size": 2,
        "limit": 1000,
        "offset": 0
    },
    "rows": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files/f2728180-6afd-4d37-8a13-f3b48069bbb6",
                "type": "files",
                "mediaType": "application/json",
            },
            "title": "birdimage",
            "filename": "birdimage.png",
            "size": 14052,
            "created": "2019-01-24 16:55:24.567",
            "createdBy": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/69f5683e-a49b-11ea-ac15-000e000000cf",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
                  "type": "employee",
                  "mediaType": "application/json",
                  "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=69f5683e-a49b-11ea-ac15-000e000000cf"
                }
            },
            "download" : {
                "downloadHref" : "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6",
                "type" : "file",
                "mediaType" : "application/octet-stream"
            },
            "miniature": {
                "href": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6?miniature=true",
                "type": "files",
                "mediaType": "image/png"
            },
            "tiny": {
                "href": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/ebb10350-0272-45db-9d33-ca5a01fd5543/t.png",
                "type": "files",
                "mediaType": "image/png"
            }
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files/933e41ac-1946-4bf0-9b21-51f2051f3e9d",
                "type": "files",
                "mediaType": "application/json",
            },
            "title": "doc",
            "filename": "doc.pdf",
            "size": 25000,
            "created": "2019-01-25 17:30:25.021",
            "createdBy": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/69f5683e-a49b-11ea-ac15-000e000000cf",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
                  "type": "employee",
                  "mediaType": "application/json",
                  "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=69f5683e-a49b-11ea-ac15-000e000000cf"
                }
            },
            "download" : {
                "downloadHref" : "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9d",
                "type" : "file",
                "mediaType" : "application/octet-stream"
            }
        }
    ]
}
```

### Добавить Файл к Операции, Номенклатуре или Контрагенту
Добавить новый Файл к Операции, Номенклатуре или Контрагенту.

#### Описание
Файлы загружается и добавляется к Файлам на основе переданного объекта JSON, 
который содержит представление нового Файла.
Результат - JSON представление обновленного списка Файлов. Для создания и добавления нового Файла к Операции, Номенклатуре или Контрагенту, 
необходимо и достаточно указать в url запросе `id` сущности, к которой добавляется Файла, и указать не пустые поля 
`filename` и `content` в переданном объекте.

В поле `content` нужно указать файл, закодированный в Base64, в поле `filename` - имя Файла с расширением.

В одном запросе можно добавить максимум 10 Файлов.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Товара c Файлами.|

> Пример добавления Файла к Товару
  
```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
    -d '[{  
       "filename": "birdimageNew.png",
       "content": "Base64"
     },{  
     "filename": "doc.pdf",
     "content": "Base64"
   }]'
```

> Response 200 (application/json)
Успешный запрос. Результат - массив всех Файлов Товара.

```json
[
  {
      "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files/f2728180-6afd-4d37-8a13-f3b48069bbb6",
          "type": "files",
          "mediaType": "application/json",
          "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6"
      },
      "title": "birdimage",
      "filename": "birdimage.png",
      "size": 14052,
      "created": "2019-01-24 16:55:24.567",
      "createdBy": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/69f5683e-a49b-11ea-ac15-000e000000cf",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
            "type": "employee",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=69f5683e-a49b-11ea-ac15-000e000000cf"
          }
      },
      "download" : {
          "downloadHref" : "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6",
          "type" : "file",
          "mediaType" : "application/octet-stream"
      },
      "miniature": {
          "href": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6?miniature=true",
          "type": "files",
          "mediaType": "image/png"
      },
      "tiny": {
          "href": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/ebb10350-0272-45db-9d33-ca5a01fd5543/t.png",
          "type": "files",
          "mediaType": "image/png"
      }
  },
  {
      "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
          "type": "files",
          "mediaType": "application/json",
          "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f"
      },
      "title": "doc",
      "filename": "doc.pdf",
      "size": 25000,
      "created": "2019-01-25 17:30:25.021",
      "createdBy": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/69f5683e-a49b-11ea-ac15-000e000000cf",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
            "type": "employee",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=69f5683e-a49b-11ea-ac15-000e000000cf"
          }
      },
      "download" : {
          "downloadHref" : "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
          "type" : "file",
          "mediaType" : "application/octet-stream"
      }
  }
]
```

### Удалить Файл

При удалении Файла удаляется первый найденный с данным идентификатором Файла у Операции, Номенклатуры или Контрагента.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Товара c Файлом.|
|idFile |  `string` (required) *Example: 19f1edc0-fc42-4001-94cb-c9ec9c62ec10* id Файла.|

> Запрос на удаление Файла у Товара.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19/files/19f1edc0-fc42-4001-94cb-c9ec9c62ec10"
  -H "Authorization: Basic <Credentials>"
```
> Response 200 (application/json)
Успешное удаление Файла.