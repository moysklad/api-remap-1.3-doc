## Розничная смена

### Розничные смены 
Средствами JSON API можно запрашивать списки Розничных смен и сведения по отдельным Розничным сменам. Кодом сущности для Розничной смены в составе JSON API является ключевое слово **retailshift**.


#### Атрибуты смены

| Название  | Тип | Описание                    | Свойство поля в запросе| Обязательное при ответе|Expand|
| --------- |:----|:----------------------------|:----------------|:------------------------|:------------------------|
|**meta**               |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Розничной смены|Только для чтения|да|нет
|**id**                 |UUID|ID Розничной смены|Только для чтения|да|нет
|**accountId**          |UUID| ID учетной записи|Только для чтения|да|нет
|**syncId**             |UUID|ID синхронизации. После заполнения недоступен для изменения|Только для чтения|нет|нет
|**updated**            |DateTime|Момент последнего обновления Розничной смены|&mdash;|да|нет
|**deleted**            |DateTime|Момент последнего удаления Розничной смены|Только для чтения|нет|нет
|**name**              |String(255)|Наименование Розничной смены|&mdash;|да|нет
|**description**        |String(4096)|Комментарий Розничной смены|&mdash;|нет|нет
|**externalCode**       |String(255)|Внешний код Розничной смены|&mdash;| да|нет
|**moment**             |DateTime|Дата смены|&mdash;|да|нет
|**vatEnabled**         |Boolean|Учитывается ли НДС|Только для чтения|да|нет
|**vatIncluded**        |Boolean| Включен ли НДС в цену|Только для чтения|нет|нет
|**owner**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Владелец (Сотрудник)|Только для чтения|да|да
|**shared**             |Boolean|Общий доступ|Только для чтения|да|нет
|**group**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Отдел сотрудника|Только для чтения|да|да
|**organization**       |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные юрлица|необходимо при создании|да|да
|**agent**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные контрагента|Только для чтения|нет|да
|**store**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада|Необходимо при создании|да|да
|**contract**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные договора|Только для чтения|нет|да
|**organizationAccount**|[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные счета юрлица|Только для чтения|нет|да
|**agentAccount**       |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные счета контрагента|Только для чтения|нет|да
|**attributes**         |Array(Object)|Коллекция метаданных доп. полей. [Поля объекта](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi) |&mdash;|нет|нет
|**files**              |MetaArray|Метаданные массива [Файлов](../dictionaries/#suschnosti-fajly) (Максимальное количество файлов - 100)|&mdash;|да|да
|**created**            |DateTime|Дата создания|Только для чтения|да|нет
|**printed**            |Boolean|Напечатан ли документ|Только для чтения|да|нет
|**published**          |Boolean|Опубликован ли документ|&mdash;|да|нет
|**closeDate**          |DateTime|Дата закрытия смены|&mdash;|нет|нет
|**proceedsNoCash**     |Float|Выручка безнал|Только для чтения|да|нет
|**proceedsCash**       |Float|Выручка наличными|Только для чтения|да|нет
|**receivedNoCash**     |Float|Получено безнал|Только для чтения|да|нет
|**receivedCash**       |Float|Получено наличными|Только для чтения|да|нет
|**retailStore**        |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные точки продаж|Необходимо при создании|да|да
|**operations**         |Array(Object)|Коллекция метаданных связанных операций|Только для чтения|да|да
|**paymentOperations**  |Array(Object)|Коллекция метаданных платежных операций|Только для чтения|нет|да
|**cheque**             |Object| информация о розничной смене  [Поля объекта](../documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-informaciq-o-roznichnoj-smene) |&mdash;|да|нет
|**acquire**            |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Банка-эквайера по операциям по карте|&mdash;| да|да
|**bankPercent**        |Int|Комиссия банка-эквайера по операциям по карте (в процентах)|&mdash;| нет|нет
|**qrAcquire**          |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные Банка-эквайера по операциям по QR-коду|&mdash;|нет|да
|**qrBankPercent**      |Double|Комиссия банка-эквайера по операция по QR-коду (в процентах)|&mdash;| нет|нет

О работе с доп. полями Розничных смен можно прочитать [здесь](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)

#### информация о розничной смене
Название      | Тип  | Описание                    | Свойство поля в запросе| Обязательное при ответе|Expand|
| ----------- |:-----|:----------------------------|:-----------------------|:-----------------------|:-----|
| **start**   |Object|информация об открытии розничной смены [Поля объекта](../documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-informaciq-ob-otkrytii-roznichnoj-smeny) |&mdash;                 |нет                     |нет
| **end**     |Object|информация о закрытии  розничной смены [Поля объекта](../documents/#dokumenty-roznichnaq-smena-roznichnye-smeny-informaciq-o-zakrytii-roznichnoj-smeny)  |&mdash;                 |нет                     |нет

#### информация об открытии розничной смены
Название             | Тип | Описание                          | Свойство поля в запросе| Обязательное при ответе|Expand|
| ------------------ |:----|:----------------------------------|:-----------------------|:------------------------|:----|
| **fnNumber**       |String(255)|номер ФН                     |&mdash;                 |нет                      |нет
| **kktRegNumber**   |String(255)|регистрационный номер ККТ    |&mdash;                 |нет                      |нет
| **fiscalDocSign**  |String(255)|фискальный признак документа |&mdash;                 |нет                      |нет
| **shiftNumber**    |String(255)|номер смены                  |&mdash;                 |нет                      |нет
| **fiscalDocNumber**|String(255)|номер фискального документа  |&mdash;                 |нет                      |нет
| **time**           |DateTime   |дата и время открытия смены. |&mdash;                 |нет                      |нет


#### информация о закрытии  розничной смены
Название             | Тип | Описание                          | Свойство поля в запросе| Обязательное при ответе|Expand|
| ------------------ |:----|:----------------------------------|:-----------------------|:------------------------|:----|
| **fnNumber**       |String(255)|номер ФН                     |&mdash;                 |нет                      |нет
| **kktRegNumber**   |String(255)|регистрационный номер ККТ    |&mdash;                 |нет                      |нет
| **fiscalDocSign**  |String(255)|фискальный признак документа |&mdash;                 |нет                      |нет
| **shiftNumber**    |String(255)|номер смены                  |&mdash;                 |нет                      |нет
| **chequesTotal**   |String(255)|количество чеков за смену    |&mdash;                 |нет                      |нет
| **fiscalDocNumber**|String(255)|номер фискального документа  |&mdash;                 |нет                      |нет
| **time**           |DateTime   |дата и время открытия смены. |&mdash;                 |нет                      |нет


### Получить Розничные смены 
Запрос на получение списка всех Розничных смен на данной учетной записи.
Результат успешного запроса - JSON представление списка Розничных смен с перечисленными полями:

| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
**meta** |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные о выдаче,
**context** | [Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye) | Метаданные о сотруднике, выполнившем запрос.
**rows** |Array(Object)|Массив JSON объектов, представляющих собой [Розничные смены](../dictionaries/#suschnosti-valuta).

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|**limit** |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|**offset** |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить Розничные смены

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/"
  -H "Authorization: Basic <Credentials>"
```
 
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка Розничных смен.

```json
{
  "context": {
    "employee": {
      "href": "https://online.moysklad.ru/api/remap/1.3/context/employee",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift",
    "type": "retailshift",
    "mediaType": "application/json",
    "size": 5,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/0b2b2caf-055e-11e6-9464-e4de0000007c",
        "type": "retailshift",
        "mediaType": "application/json"
      },
      "id": "0b2b2caf-055e-11e6-9464-e4de0000007c",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
      "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
      "updated": "2016-04-18 15:07:12",
      "name": "00001",
      "externalCode": "iR5ZTLzfhK98uzqIFbC871",
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
      "moment": "2016-04-18 15:06:51",
      "vatEnabled": true,
      "vatIncluded": true,
      "organization": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
          "type": "organization",
          "mediaType": "application/json"
        }
      },
      "store": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/850ee995-f504-11e5-8a84-bae500000160",
          "type": "store",
          "mediaType": "application/json"
        }
      },
      "organizationAccount": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/account/3a30e844-016f-11e6-9464-e4de00000068",
          "type": "account",
          "mediaType": "application/json"
        }
      },
      "attributes": [
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata/attributes/0cd74e1e-2e59-11e6-8a84-bae50000008a",
            "type": "attributemetadata",
            "mediaType": "application/json"
          },
          "id": "bb08dccf-0bd2-11e6-9464-e4de000000ae",
          "name": "AttributeName1",
          "type": "string",
          "value": "Да"
        }
      ],
      "closeDate": "2016-04-18 15:07:12",
      "proceedsNoCash": 0,
      "proceedsCash": 5100,
      "receivedNoCash": 0,
      "receivedCash": 5136,
      "retailStore": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailstore/851f8576-f504-11e5-8a84-bae50000016c",
          "type": "retailstore",
          "mediaType": "application/json"
        }
      },
      "operations": [
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/29547f06-ec69-11e7-0532-9eed0000001b",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/metadata",
            "type": "retaildemand",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildemand/edit?id=29547f06-ec69-11e7-0532-9eed0000001b"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/3395a278-ec69-11e7-0532-9eed00000022",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/metadata",
            "type": "retailsalesreturn",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retailsalesreturn/edit?id=3395a278-ec69-11e7-0532-9eed00000022"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/2eb3c0ad-f9d9-11e7-0532-9eed0000005a",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/metadata",
            "type": "retaildrawercashin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashin/edit?id=2eb3c0ad-f9d9-11e7-0532-9eed0000005a"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/3d8258c5-f9d9-11e7-0532-9eed0000005e",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/metadata",
            "type": "retaildrawercashout",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashout/edit?id=3d8258c5-f9d9-11e7-0532-9eed0000005e"
          }
        }
      ],
      "paymentOperations": [
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/6c3237ff-f9d9-11e7-0532-9eed00000086",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/metadata",
            "type": "cashin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#cashin/edit?id=6c3237ff-f9d9-11e7-0532-9eed00000086"
          },
          "linkedSum": 0
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/5952a2fb-f9d8-11e7-0532-9eed00000036",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/metadata",
            "type": "paymentin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#paymentin/edit?id=5952a2fb-f9d8-11e7-0532-9eed00000036"
          },
          "linkedSum": 0
        }
      ]
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/cd86df19-0563-11e6-9464-e4de0000008e",
        "type": "retailshift",
        "mediaType": "application/json"
      },
      "id": "cd86df19-0563-11e6-9464-e4de0000008e",
      "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
      "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
      "updated": "2016-04-18 15:48:19",
      "name": "00002",
      "externalCode": "uhM2bdwAg7661Qhx3f7102",
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
      "moment": "2016-04-18 15:48:04",
      "created": "2016-08-25 19:55:00",
      "printed": true,
      "published": true,
      "vatEnabled": true,
      "vatIncluded": true,
      "organization": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
          "type": "organization",
          "mediaType": "application/json"
        }
      },
      "store": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/850ee995-f504-11e5-8a84-bae500000160",
          "type": "store",
          "mediaType": "application/json"
        }
      },
      "organizationAccount": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/account/3a30e844-016f-11e6-9464-e4de00000068",
          "type": "account",
          "mediaType": "application/json"
        }
      },
      "attributes": [
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata/attributes/0cd74e1e-2e59-11e6-8a84-bae50000008a",
            "type": "attributemetadata",
            "mediaType": "application/json"
          },
          "id": "bb08dccf-0bd2-11e6-9464-e4de000000ae",
          "name": "AttributeName1",
          "type": "string",
          "value": "Да"
        }
      ],
      "closeDate": "2016-04-18 15:48:19",
      "proceedsNoCash": 1800,
      "proceedsCash": 0,
      "receivedNoCash": 0,
      "receivedCash": 0,
      "retailStore": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailstore/851f8576-f504-11e5-8a84-bae50000016c",
          "type": "retailstore",
          "mediaType": "application/json"
        }
      },
      "operations": [
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/29547f06-ec69-11e7-0532-9eed0000002c",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/metadata",
            "type": "retaildemand",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildemand/edit?id=29547f06-ec69-11e7-0532-9eed0000002c"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/3395a278-ec69-11e7-0532-9eed00000033",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/metadata",
            "type": "retailsalesreturn",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retailsalesreturn/edit?id=3395a278-ec69-11e7-0532-9eed00000033"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/2eb3c0ad-f9d9-11e7-0532-9eed0000006b",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/metadata",
            "type": "retaildrawercashin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashin/edit?id=2eb3c0ad-f9d9-11e7-0532-9eed0000006b"
          }
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/3d8258c5-f9d9-11e7-0532-9eed0000006a",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/metadata",
            "type": "retaildrawercashout",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashout/edit?id=3d8258c5-f9d9-11e7-0532-9eed0000006a"
          }
        }
      ],
      "paymentOperations": [
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/6c3237ff-f9d9-11e7-0532-9eed00000099",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/metadata",
            "type": "cashin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#cashin/edit?id=6c3237ff-f9d9-11e7-0532-9eed00000099"
          },
          "linkedSum": 0
        },
        {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/5952a2fb-f9d8-11e7-0532-9eed00000048",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/metadata",
            "type": "paymentin",
            "mediaType": "application/json",
            "uuidHref": "http://online.moysklad.ru/app/#paymentin/edit?id=5952a2fb-f9d8-11e7-0532-9eed00000048"
          },
          "linkedSum": 0
        }
      ]
    }
  ]
}
```
### Создать розничную смену
Запрос на создание новой розничной смены.
Обязательные для создания поля:

| Название  | Тип | Описание                    |
| --------- |:----|:----------------------------|
|**organization**       |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные юрлица
|**store**              |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные склада
|**retailStore**        |[Meta](../#mojsklad-json-api-obschie-swedeniq-metadannye)|Метаданные точки продаж


> Пример создания новой розничной смены с телом запроса, содержащим только необходимые поля.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.2/entity/retailshift"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "organization": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.2/entity/organization/011d87bc-fade-11eb-ac1b-000f00000087",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.2/entity/organization/metadata",
                   "type": "organization",
                    "mediaType": "application/json"
                  }
            },
            "store": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.2/entity/store/012493aa-fade-11eb-ac1b-000f00000089",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.2/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
                }
            },
            "retailStore": {
                 "meta": {
                     "href": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/01610ea7-fade-11eb-ac1b-000f0000009f",
                     "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/metadata",
                     "type": "retailstore",
                     "mediaType": "application/json"
                  }
            }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной розничной смены.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.2/entity/retailshift/85f03d49-fff0-11eb-ac1b-000a00000000",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/retailshift/metadata",
    "type": "retailshift",
    "mediaType": "application/json",
    "uuidHref": "https://online.moysklad.ru/app/#retailshift/edit?id=85f03d49-fff0-11eb-ac1b-000a00000000"
  },
  "id": "85f03d49-fff0-11eb-ac1b-000a00000000",
  "accountId": "46683bcd-fb43-11eb-ac1b-001000000001",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/employee/00d60a2a-fade-11eb-ac1b-000f0000004b",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=00d60a2a-fade-11eb-ac1b-000f0000004b"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/group/466c89ae-fb43-11eb-ac1b-001000000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2021-08-18 09:50:05.517",
  "name": "00005",
  "externalCode": "-co-jXf3gIbPPIcO006uZ3",
  "moment": "2021-08-18 09:50:00.000",
  "store": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/store/012493aa-fade-11eb-ac1b-000f00000089",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#warehouse/edit?id=012493aa-fade-11eb-ac1b-000f00000089"
    }
  },
  "agent": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/01560dcb-fade-11eb-ac1b-000f0000009d",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#company/edit?id=01560dcb-fade-11eb-ac1b-000f0000009d"
    }
  },
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/organization/011d87bc-fade-11eb-ac1b-000f00000087",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#mycompany/edit?id=011d87bc-fade-11eb-ac1b-000f00000087"
    }
  },
  "created": "2021-08-18 09:50:06.852",
  "printed": false,
  "published": false,
  "files": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/retailshift/85f03d49-fff0-11eb-ac1b-000a00000000/files",
      "type": "files",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },
  "agent": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/01560dcb-fade-11eb-ac1b-000f0000009d",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#company/edit?id=01560dcb-fade-11eb-ac1b-000f0000009d"
    }
  },
  "proceedsNoCash": 0.0,
  "proceedsCash": 0.0,
  "receivedNoCash": 0.0,
  "receivedCash": 0.0,
  "retailStore": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/01610ea7-fade-11eb-ac1b-000f0000009f",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/metadata",
      "type": "retailstore",
      "mediaType": "application/json",
      "uuidHref": "https://online.moysklad.ru/app/#retailstore/edit?id=01610ea7-fade-11eb-ac1b-000f0000009f"
    }
  }
}
```

### Изменить розничную смену
Запрос на обновление розничной смены с указанным id.

**Параметры**

|Параметр   |Описание   | 
|:----|:----|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Розничной смены.|

> Пример запроса на обновление розничной смены.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.2/entity/retailshift/83f34607-ff35-11eb-ac1b-000c00000000"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
    "name": "0001",
    "moment": "2021-08-17 16:56:52",
    "closeDate": "2021-08-21 16:56:52",
    "organization": {
         "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.2/entity/organization/b4343660-0016-11ec-ac12-000b000000d7",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/organization/metadata",
            "type": "organization",
            "mediaType": "application/json"
         }
    },
    "store": {
      "meta": {
       "href": "https://online.moysklad.ru/api/remap/1.2/entity/store/7421cf1a-0016-11ec-ac12-000b00000080",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/store/metadata",
                "type": "store",
                "mediaType": "application/json"
                }
            },
            "acquire": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/74221ae8-0016-11ec-ac12-000b00000081",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/counterparty/metadata",
            "type": "counterparty",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#company/edit?id=74221ae8-0016-11ec-ac12-000b00000081"
        }
    },
            "bankPercent": 22.0,
            "qrBankPercent": 0.0,
            "retailstore": {
                 "meta": {
                     "href": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/01610ea7-fade-11eb-ac1b-000f0000009f",
                     "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/retailstore/metadata",
                     "type": "retailstore",
                     "mediaType": "application/json"
                  }
            },
             "cheque": {
        "start": {
            "shiftNumber": "3456",
            "kktRegNum": "5678",
            "fnNumber": "1234",
            "fiscalDocNumber": "7890",
            "fiscalDocSign": "9012",
            "time": "2021-08-17 16:56:52"
        },
        "end": {
            "shiftNumber": "2109",
            "kktRegNum": "0987",
            "fnNumber": "4321",
            "fiscalDocNumber": "8765",
            "fiscalDocSign": "6543",
            "time": "2021-08-21 16:56:52",
            "chequesTotal": 15,
            "fiscalDocsTotal": 17
           }       
       }
   } '  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленной розничной смены.

```json
{
  "meta": {
    "href": "http://localhost/api/remap/1.2/entity/retailshift/49819758-0017-11ec-ac12-000a00000000",
    "metadataHref": "http://localhost/api/remap/1.2/entity/retailshift/metadata",
    "type": "retailshift",
    "mediaType": "application/json",
    "uuidHref": "http://localhost/app/#retailshift/edit?id=49819758-0017-11ec-ac12-000a00000000"
  },
  "id": "49819758-0017-11ec-ac12-000a00000000",
  "accountId": "73215387-0016-11ec-ac12-000c00000001",
  "owner": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/employee/73d6e937-0016-11ec-ac12-000b00000042",
      "metadataHref": "http://localhost/api/remap/1.2/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json",
      "uuidHref": "http://localhost/app/#employee/edit?id=73d6e937-0016-11ec-ac12-000b00000042"
    }
  },
  "shared": false,
  "group": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/group/73230224-0016-11ec-ac12-000c00000002",
      "metadataHref": "http://localhost/api/remap/1.2/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2021-08-18 18:43:40.740",
  "name": "0001",
  "externalCode": "srR4xJ90hAOHZPHrsSCS51",
  "moment": "2021-08-17 16:56:00.000",
  "store": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/store/7421cf1a-0016-11ec-ac12-000b00000080",
      "metadataHref": "http://localhost/api/remap/1.2/entity/store/metadata",
      "type": "store",
      "mediaType": "application/json",
      "uuidHref": "http://localhost/app/#warehouse/edit?id=7421cf1a-0016-11ec-ac12-000b00000080"
    }
  },
  "organization": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/organization/b4343660-0016-11ec-ac12-000b000000d7",
      "metadataHref": "http://localhost/api/remap/1.2/entity/organization/metadata",
      "type": "organization",
      "mediaType": "application/json",
      "uuidHref": "http://localhost/app/#mycompany/edit?id=b4343660-0016-11ec-ac12-000b000000d7"
    }
  },
  "created": "2021-08-18 14:27:35.862",
  "printed": false,
  "published": false,
  "files": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/retailshift/49819758-0017-11ec-ac12-000a00000000/files",
      "type": "files",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },
  "closeDate": "2021-08-21 16:56:00.000",
  "proceedsNoCash": 0.0,
  "proceedsCash": 0.0,
  "receivedNoCash": 0.0,
  "receivedCash": 0.0,
  "cheque": {
    "start": {
      "shiftNumber": "3456",
      "fnNumber": "1234",
      "fiscalDocNumber": "7890",
      "fiscalDocSign": "9012",
      "time": "2021-08-17 16:56:00.000"
    },
    "end": {
      "shiftNumber": "2109",
      "fnNumber": "4321",
      "fiscalDocNumber": "8765",
      "fiscalDocSign": "6543",
      "time": "2021-08-21 16:56:00.000",
      "chequesTotal": 15,
      "fiscalDocsTotal": 17
    }
  },
  "retailStore": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/retailstore/74940da1-0016-11ec-ac12-000b00000096",
      "metadataHref": "http://localhost/api/remap/1.2/entity/retailstore/metadata",
      "type": "retailstore",
      "mediaType": "application/json",
      "uuidHref": "http://localhost/app/#retailstore/edit?id=74940da1-0016-11ec-ac12-000b00000096"
    }
  },
  "acquire": {
    "meta": {
      "href": "http://localhost/api/remap/1.2/entity/counterparty/74221ae8-0016-11ec-ac12-000b00000081",
      "metadataHref": "http://localhost/api/remap/1.2/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json",
      "uuidHref": "http://localhost/app/#company/edit?id=74221ae8-0016-11ec-ac12-000b00000081"
    }
  },
  "bankPercent": 0.0,
  "qrBankPercent": 0.0
}
```

### Удалить Розничную смену

**Параметры**

|Параметр   |Описание   | 
|:----|:----|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Розничной смены.|

> Запрос на удаление Розничной смены с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление Розничной смены.

### Метаданные Розничных смен 
#### Метаданные Розничных смен 
Запрос на получение метаданных Розничных смен. Результат - объект JSON, включающий в себя:

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
| **meta**         | Ссылка на метаданные Розничных смен|
| **attributes**   | Массив объектов доп. полей Розничных смен в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)|
| **createShared** | создавать новые Розничные смены с меткой "Общий"|

Структура отдельного объекта, представляющего доп. поле подробно описана в разделе [Работа с дополнительными полями](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi).

> Метаданные Розничных смен

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление доп. полей Розничных продаж.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata",
    "mediaType": "application/json"
  },
  "attributes": [
    {
      "id": "bb08dccf-0bd2-11e6-9464-e4de000000ae",
      "name": "AttributeName1",
      "type": "string",
      "required": false
    }
  ],
  "createShared": false
}
```

### Отдельное доп. поле

**Параметры**

|Параметр   |Описание   | 
|:----|:----|
|**id** |  `string` (required) *Example: 5290a290-0313-11e6-9464-e4de00000020* id Доп. поля.|
 
#### Отдельное доп. поле
 
> Запрос на получение информации по отдельному дополнительному полю.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata/attributes/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного доп. поля.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata/attributes/d335f74e-558c-11e6-8a84-bae50000009a",
    "type": "attributemetadata",
    "mediaType": "application/json"
  },
  "id": "d335f74e-558c-11e6-8a84-bae50000009a",
  "name": "AttributeName1",
  "type": "file",
  "required": false
}
```

#### Розничная смена

**Параметры**

|Параметр   |Описание   | 
|:----|:----|
|**id** |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Розничной смены.|

### Получить Розничную смену 

> Запрос на получение отдельной Розничной смены с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Розничной смены.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/91a42d66-0ad2-11e6-9464-e4de00000017",
    "type": "retailshift",
    "mediaType": "application/json"
  },
  "id": "91a42d66-0ad2-11e6-9464-e4de00000017",
  "accountId": "84e60e93-f504-11e5-8a84-bae500000008",
  "syncId": "734a9e26-45a2-4ead-849c-e144daeb854d",
  "updated": "2016-04-25 13:50:05",
  "name": "00004",
  "externalCode": "33Ox0o1GjpDZC9x41fUA11",
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
  "moment": "2016-04-25 13:10:19",
  "created": "2016-08-25 19:55:00",
  "printed": true,
  "published": true,
  "vatEnabled": true,
  "vatIncluded": true,
  "organization": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/organization/850c8195-f504-11e5-8a84-bae50000015e",
      "type": "organization",
      "mediaType": "application/json"
    }
  },
  "store": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/store/850ee995-f504-11e5-8a84-bae500000160",
      "type": "store",
      "mediaType": "application/json"
    }
  },
  "organizationAccount": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/account/3a30e844-016f-11e6-9464-e4de00000068",
      "type": "account",
      "mediaType": "application/json"
    }
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailshift/metadata/attributes/0cd74e1e-2e59-11e6-8a84-bae50000008a",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "bb08dccf-0bd2-11e6-9464-e4de000000ae",
      "name": "AttributeName1",
      "type": "string",
      "value": "Да"
    }
  ],
  "closeDate": "2016-04-25 13:10:19",
  "proceedsNoCash": 0,
  "proceedsCash": 0,
  "receivedNoCash": 0,
  "receivedCash": 0,
  "retailStore": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/retailstore/851f8576-f504-11e5-8a84-bae50000016c",
      "type": "retailstore",
      "mediaType": "application/json"
    }
  },
  "operations": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/29547f06-ec69-11e7-0532-9eed0000001b",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildemand/metadata",
        "type": "retaildemand",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#retaildemand/edit?id=29547f06-ec69-11e7-0532-9eed0000001b"
      }
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/3395a278-ec69-11e7-0532-9eed00000022",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retailsalesreturn/metadata",
        "type": "retailsalesreturn",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#retailsalesreturn/edit?id=3395a278-ec69-11e7-0532-9eed00000022"
      }
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/2eb3c0ad-f9d9-11e7-0532-9eed0000005a",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashin/metadata",
        "type": "retaildrawercashin",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashin/edit?id=2eb3c0ad-f9d9-11e7-0532-9eed0000005a"
      }
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/3d8258c5-f9d9-11e7-0532-9eed0000005e",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/retaildrawercashout/metadata",
        "type": "retaildrawercashout",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#retaildrawercashout/edit?id=3d8258c5-f9d9-11e7-0532-9eed0000005e"
      }
    }
  ],
  "paymentOperations": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/6c3237ff-f9d9-11e7-0532-9eed00000086",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/cashin/metadata",
        "type": "cashin",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#cashin/edit?id=6c3237ff-f9d9-11e7-0532-9eed00000086"
      },
      "linkedSum": 0
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/5952a2fb-f9d8-11e7-0532-9eed00000036",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/paymentin/metadata",
        "type": "paymentin",
        "mediaType": "application/json",
        "uuidHref": "http://online.moysklad.ru/app/#paymentin/edit?id=5952a2fb-f9d8-11e7-0532-9eed00000036"
      },
      "linkedSum": 0
    }
  ]
}
```
