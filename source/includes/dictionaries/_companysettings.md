## Настройки компании

На данный момент можно получить информацию о текущих настройках компании и типах цен товаров. 

#### Настройки компании 
#### Атрибуты сущности

| Название  | Тип | Описание                    | Свойство поля в запросе | Обязательное при ответе|Expand|
| --------- |:----|:----------------------------|:----------------|:------------------------|:------------------------|
|**meta**                |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Настроек компании|&mdash;|да|нет
|**currency**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные стандартной валюты|&mdash;|да|нет
|**priceTypes**          |Array(Object)|Коллекция всех существующих типов цен. [Подробнее тут](../dictionaries/#suschnosti-nastrojki-kompanii-izmenit-proekt-tip-ceny)|&mdash;|да|нет
|**discountStrategy**    |Enum|Совместное применение скидок. [Подробнее тут](../dictionaries/#suschnosti-nastrojki-kompanii-izmenit-proekt-sowmestnoe-primenenie-skidok)|Необходимое при создании|да|нет
|**globalOperationNumbering**|Boolean|Использовать сквозную нумерацию документов. Если проставлен true, будет установлена сквозная нумерация за всю историю, иначе нумерация документов будет начинаться заново каждый календарный год.|&mdash;|да|нет
|**checkShippingStock**|Boolean|Запретить отгрузку отсутствующих товаров. Если запрет установлен (true значение), пользователи не смогут провести отгрузку со склада отсутствующих товаров.|&mdash;|да|нет
|**checkMinPrice**|Boolean|Автоматически устанавливать минимальную цену. Если включено, при сохранении документов продажи с ценами меньше минимальных цен (указанных в карточках товара) цены будут автоматически увеличены до минимальных.|&mdash;|да|нет
|**useRecycleBin**|Boolean|Использовать корзину. Если включено, то все документы при удалении будут помещаться в корзину. Также появится возможность восстанавливать ошибочно удаленные документы.|&mdash;|да|нет
|**useCompanyAddress** |Boolean|Использовать адрес компании для электронных писем. Если включено, письма будут отправляться с адреса, указанного в companyAddress, иначе письма будут отправляться с адреса пользователя.|&mdash;|да|нет
|**companyAddress**|String(255)|Адрес компании для электронных писем|&mdash;|нет|нет

#### Тип цены
Структура отдельного объекта, представляющего тип цены:

| Название  | Тип | Описание                    | Свойство поля в запросе | Обязательное при ответе|Expand|
| --------- |:----|:----------------------------|:----------------|:------------------------|:------------------------|
|**meta**             |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Типа цены|Только для чтения|да|нет
|**id**               |UUID|ID Типа цены|Только для чтения|да|нет
|**name**             |String(255)|Наименование Типа цены|Необходимое при создании|да|нет
|**externalCode**     |String(255)|Внешний код Типа цены|&mdash;|да|нет

#### Совместное применение скидок
Перечисление значений, представляющих совместное применение скидок:

| Название | Описание|
| ------------------------------ |:---------------------------|
| **bySum**               | Сумма скидок. Означает, что должна действовать сумма скидок.                     |
| **byPriority**          | Приоритетная. Должна действовать одна, наиболее выгодная для покупателя скидка.  |

#### Метаданные настроек
В метаданных Настроек компании, в поле **customEntities** показан список пользовательских справочников.
Каждый пользовательский справочник содержит поля:

| Название  | Тип | Описание                    | Свойство поля в запросе | Обязательное при ответе|Expand|
| --------- |:----|:----------------------------|:----------------|:------------------------|:------------------------|
|**meta**                |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Пользовательского справочника|Только для чтения|да|нет
|**entityMeta**               |URL|Ссылка на список сущностей данного пользовательского справочника|&mdash;|нет|нет
|**name**               |String(255)|Наименование справочника|&mdash;|нет|нет

### Получить Настройки компании 
> Запрос на получение Настроек компании.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/context/companysettings"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Настроек компании.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata",
    "type": "companysettings",
    "mediaType": "application/json"
  },
  "currency": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/45ffbac2-24a5-11e6-8a84-bae500000055",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
      "type": "currency",
      "mediaType": "application/json"
    },
    "id": "45ffbac2-24a5-11e6-8a84-bae500000055",
    "system": true,
    "name": "руб",
    "fullName": "Российский рубль",
    "rate": 1,
    "multiplicity": 1,
    "indirect": false,
    "rateUpdateType": "manual",
    "code": "643",
    "isoCode": "RUB",
    "majorUnit": {
      "gender": "masculine",
      "s1": "рубль",
      "s2": "рубля",
      "s5": "рублей"
    },
    "minorUnit": {
      "gender": "feminine",
      "s1": "копейка",
      "s2": "копейки",
      "s5": "копеек"
    },
    "archived": false,
    "default": true
  },
  "priceTypes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "type": "pricetype",
        "mediaType": "application/json"
      },
      "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
      "name": "Цена для друзей",
      "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f4444",
        "type": "pricetype",
        "mediaType": "application/json"
      },
      "id": "672559f1-cbf3-11e1-9eb9-889ffa6f4444",
      "name": "Цена для конкурентов",
      "externalCode": "cbcf493b-55bc-11d9-848a-00112f434444"
    }
  ],
  "discountStrategy": "bySum",
   "globalOperationNumbering": true,
   "checkShippingStock": true,
   "checkMinPrice": true,
   "useRecycleBin": true,
   "useCompanyAddress": true,
   "companyAddress": "MyCompany@moysklad.ru"
}
```

### Изменить Настройки компании
 Редактировать можно следующие настройки компании:

| Название  | Тип | Описание                    
| --------- |:----|:----------------------------|
|**discountStrategy**    |Enum|Совместное применение скидок. [Подробнее тут](../dictionaries/#suschnosti-nastrojki-kompanii-izmenit-proekt-sowmestnoe-primenenie-skidok)
|**globalOperationNumbering**|Boolean|Использовать сквозную нумерацию документов. Если проставлен true, будет установлена сквозная нумерация за всю историю, иначе нумерация документов будет начинаться заново каждый календарный год.
|**checkShippingStock**|Boolean|Запретить отгрузку отсутствующих товаров. Если запрет установлен (true значение), пользователи не смогут провести отгрузку со склада отсутствующих товаров.
|**checkMinPrice**|Boolean|Автоматически устанавливать минимальную цену. Если включено, при сохранении документов продажи с ценами меньше минимальных цен (указанных в карточках товара) цены будут автоматически увеличены до минимальных.
|**useRecycleBin**|Boolean|Использовать корзину. Если включено, то все документы при удалении будут помещаться в корзину. Также появится возможность восстанавливать ошибочно удаленные документы.
|**useCompanyAddress** |Boolean|Использовать адрес компании для электронных писем. Если включено, письма будут отправляться с адреса, указанного в companyAddress, иначе письма будут отправляться с адреса пользователя.
|**companyAddress**|String(255)|Адрес компании для электронных писем|&mdash;| нет

Допускается частичное редактирование - отредактированы будут только присутствующие в запросе поля.
> Запрос на изменение Настроек компании.

```shell
curl -X PUT
  "https://online.moysklad.ru/api/remap/1.3/context/companysettings"
  -H "Authorization: Basic <Credentials>"
  -H "Content-Type: application/json"
      -d '{
	  "globalOperationNumbering": true,
	  "checkShippingStock": true,
      "checkMinPrice": true,
      "useRecycleBin": true,
      "useCompanyAddress": true,
      "companyAddress": "MyCompany@moysklad.ru",
      "discountStrategy": "bySum"
}'
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Настроек компании.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata",
    "type": "companysettings",
    "mediaType": "application/json"
  },
  "currency": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/45ffbac2-24a5-11e6-8a84-bae500000055",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
      "type": "currency",
      "mediaType": "application/json"
    },
    "id": "45ffbac2-24a5-11e6-8a84-bae500000055",
    "system": true,
    "name": "руб",
    "fullName": "Российский рубль",
    "rate": 1,
    "multiplicity": 1,
    "indirect": false,
    "rateUpdateType": "manual",
    "code": "643",
    "isoCode": "RUB",
    "majorUnit": {
      "gender": "masculine",
      "s1": "рубль",
      "s2": "рубля",
      "s5": "рублей"
    },
    "minorUnit": {
      "gender": "feminine",
      "s1": "копейка",
      "s2": "копейки",
      "s5": "копеек"
    },
    "archived": false,
    "default": true
  },
  "priceTypes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "type": "pricetype",
        "mediaType": "application/json"
      },
      "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
      "name": "Цена для друзей",
      "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f4444",
        "type": "pricetype",
        "mediaType": "application/json"
      },
      "id": "672559f1-cbf3-11e1-9eb9-889ffa6f4444",
      "name": "Цена для конкурентов",
      "externalCode": "cbcf493b-55bc-11d9-848a-00112f434444"
    }
  ],
  "discountStrategy": "bySum",
   "globalOperationNumbering": true,
   "checkShippingStock": true,
   "checkMinPrice": true,
   "useRecycleBin": true,
   "useCompanyAddress": true,
   "companyAddress": "MyCompany@moysklad.ru"
}
```


#### Метаданные настроек компании 
### Получить метаданные настроек компании 
> Запрос на получение метаданных Настроек компании.

```shell
curl -X GET
  "ttps://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление метаданных настроек компании.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings",
    "mediaType": "application/json"
  },
  "customEntities": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata/customEntities/eaacabaf-2655-11e6-8a84-bae500000045",
        "type": "customentitymetadata",
        "mediaType": "application/json"
      },
      "name": "Партнеры",
      "createShared": true
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata/customEntities/f3aff189-2655-11e6-8a84-bae500000046",
        "type": "customentitymetadata",
        "mediaType": "application/json"
      },
      "name": "Рекламные агенства",
      "createShared": true
    }
  ]
}
```
