## Сохраненные фильтры
### Сохраненный фильтр

Средствами JSON API можно получать сохраненные фильтры по id и в виде списка.
Сохраненный фильтр - это набор параметров и их значений, настраиваемых пользователями,
чтобы отфильтровать список из сущностей, документов.
Сущность представлена в виде идентификатора и наименования. Параметры фильтрации не возвращаются.

Сохраненные фильтры можно повторно применять для фильтрации списка сущностей.

Сохраненные фильтры относятся к конкретному типу сущности. 
Например, можно получить список фильтров для реестра документов Приемки, документов Входящих платежей, 
справочника Контрагентов. Нельзя получить общий список сохраненных фильтров для всех
сущностей пользователя.
Для каждого типа сущности будет свой набор параметров фильтрации.

#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|Expand|
| --------- |:----|:----------------------------|:----------------|:------------------------|:------------------------|
|**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные фильтра|&mdash;|да|нет
|**id**        |UUID|ID фильтра|Только для чтения|да|нет
|**accountId**    |UUID|ID учетной записи|Только для чтения|да|нет
|**owner**     |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Владелец (Сотрудник)|Только для чтения|да|да
|**name**    |String|Название фильтра|Необходимое при создании|да|нет

Пример запросa:
Сущности и документы - ```/entity/[entityType]/namedfilter```

### Получить список фильтров

> Пример запроса на получение списка фильтров для товаров

```shell
  curl -X GET
    "https://online.moysklad.ru/api/remap/1.3/entity/product/namedfilter"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"  
```

> Response 200 

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
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/namedfilter/",
    "type": "namedfilter",
    "mediaType": "application/json",
    "size": 1,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/namedfilter/b5863410-ca86-11eb-ac12-000d00000019",
        "type": "namedfilter",
        "mediaType": "application/json"
      },
      "owner": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/234eee6f-c513-11eb-ac12-000d0000003b",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json",
          "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=234eee6f-c513-11eb-ac12-000d0000003b"
        }
      },
      "accountId": "22ef0c54-c513-11eb-ac12-000700000002",
      "id": "b5863410-ca86-11eb-ac12-000d00000019",
      "name": "filterName"
    }
  ]
}
```

### Получить фильтр по id

**Параметры**

|Параметр   |Описание   | 
|:----|:----|
|**id** |  `string` (required) *Example: 736da682-ad8b-11eb-0a80-17ef000000d4* id Фильтра.|


> Пример запроса на получение фильтра для товара по id

```shell
  curl -X GET
    "https://online.moysklad.ru/api/remap/1.3/entity/product/namedfilter/b5863410-ca86-11eb-ac12-000d00000019"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"  
```

> Response 200 

```json
  {
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/namedfilter/b5863410-ca86-11eb-ac12-000d00000019",
    "type": "namedfilter",
    "mediaType": "application/json"
  },
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/234eee6f-c513-11eb-ac12-000d0000003b",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=234eee6f-c513-11eb-ac12-000d0000003b"
    }
  },
  "accountId": "22ef0c54-c513-11eb-ac12-000700000002",
  "id": "b5863410-ca86-11eb-ac12-000d00000019",
  "name": "filterName"
}
```

### Применение сохраненного фильтра

Средствами JSON API можно применять сохраненные фильтры ко всем [Сущностям](https://dev.moysklad.ru/doc/api/remap/1.2/dictionaries/), кроме Ассортимента, и [Документам](https://dev.moysklad.ru/doc/api/remap/1.2/documents/). 
Результатом фильтрации будет список сущностей, удовлетворяющих набору условий, сохраненных в фильтре.

Для применения фильтрации необходимо в специальном параметре запроса `namedfilter` передать ссылку на нужный сохраненный фильтр.

Пример url с применением сохраненного фильтра:
`https://online.moysklad.ru/api/remap/1.2/entity/product?namedfilter=https://online.moysklad.ru/api/remap/1.2/entity/product/namedFilter/b5863410-ca86-11eb-ac12-000d00000019`

<br>

Ограничения

- Только создатель фильтра может его применять.
- В одном запрос можно применять только один сохраненный фильтр
- Сохраненный фильтр несовместим с параметром запроса `filter`
- На эндпоинте можно применять только тот сохраненный фильтр, который можно получить через `/entity/[entityType]/namedfilter`
 
