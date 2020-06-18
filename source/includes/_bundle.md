## Комплект
### Комплекты

Средствами JSON API можно создавать и обновлять сведения о Комплектах, запрашивать списки Комплектов и сведения по отдельным Комплектам. Кодом сущности для Комплекта в составе JSON API является ключевое слово **bundle**.

#### Атрибуты сущности
+ **meta** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) объекта
+ **id** - ID Комплекта в формате UUID `Только для чтения`
+ **accountId** - ID учетной записи `Только для чтения`
+ **owner** - Ссылка на Владельца (Сотрудника) в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **shared** - Общий доступ
+ **group** - Отдел сотрудника в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **syncId** - ID синхронизации. После заполнения недоступен для изменения.
+ **updated** - Момент последнего обновления сущности `Только для чтения`
+ **name** - Наименование Комплекта `Необходимое`
+ **description** - Описание Комплекта
+ **code** - Код Комплекта
+ **externalCode** - Внешний код Комплекта
+ **archived** - Отметка о том, добавлен ли Комплект в архив
+ **pathName** - Наименование группы, в которую входит Комплект `Только для чтения`
+ **vat** - НДС %
+ **effectiveVat** - Реальный НДС % `Только для чтения`
+ **productFolder** - Ссылка на группу Комплекта
+ **uom** - Единицы измерения
+ **images** - Изображения Комплекта. Изображений у Комплекта может быть не более 10
+ **minPrice** - Минимальная цена
+ **salePrices** - Цены продажи
+ **attributes** - Коллекция доп. полей в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **country** - Ссылка на страну в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **article** - Артикул
+ **weight** - Вес
+ **volume** - Объем
+ **barcodes** - Массив штрихкодов Комплекта
+ **discountProhibited** - Признак запрета скидок.
+ **overhead** - Дополнительные расходы
  - **currency** - Валюта доп расходов
  - **value** - Значение доп расходов
+ **components** - Компоненты Комплекта
+ **trackingType** - Тип маркируемой продукции
  + **NOT_TRACKED** - Без маркировки
  + **TOBACCO** - Тип маркировки "Табак"
  + **SHOES** - Тип маркировки "Обувь"
+ **tnved** - Код ТН ВЭД
+ **paymentItemType** - Признак предмета расчета
  + **GOOD** - Товар
  + **EXCISABLE_GOOD** - Подакцизный товар
  + **COMPOUND_PAYMENT_ITEM** - Составной предмет расчета
  + **ANOTHER_PAYMENT_ITEM** - Иной предмет расчета
+ **taxSystem** - Код системы налогообложения
  + **TAX_SYSTEM_SAME_AS_GROUP** - Совпадает с группой
  + **GENERAL_TAX_SYSTEM** - ОСН
  + **SIMPLIFIED_TAX_SYSTEM_INCOME** - УСН. Доход
  + **SIMPLIFIED_TAX_SYSTEM_INCOME_OUTCOME** - УСН. Доход-Расход
  + **UNIFIED_AGRICULTURAL_TAX** - ЕСХН
  + **PRESUMPTIVE_TAX_SYSTEM** - ЕНВД
  + **PATENT_BASED** - Патент

##### Минимальная цена
+ **value** - Значение цены
+ **currency** - Ссылка на валюту в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

#### Компоненты Комплекта
Компоненты Комплекта - это список товаров/услуг/модификаций, который входят в состав комплекта. Компонентов у комплекта может быть от 1 до 50.
Объект компонента Комплекта содержит следующие поля:

+ **id** - ID компонента в формате UUID `Только для чтения`
+ **accountId** - ID учетной записи `Только для чтения`
+ **quantity** - Количество товаров/услуг данного вида в компоненте. Максимальное количество знаков 12, округляется до 4х знаков после запятой.
+ **assortment** - Ссылка на товар/услугу/серию, которую представляет собой компонент.


#### Комплект как позиция документа
Комплект может выступать в роли позиции документа. Он также как и товары, услуги и модификации может быть передан в составе позиции в формате метаданных.<br>
Вот некоторые ограничения, связанные с использованием комплектов как позиций:

+ Количество комплектов должно быть целым числом
+ Комплекты не могут быть позициями в следующих типах документов:
  - Заказы поставщикам
  - Счета поставщиков
  - Приемки
  - Возвраты поставщикам
  - Выданные отчеты комиссионера
  - Списания
  - Оприходования
  - Перемещения
  - Инвентаризации
  - Тех. карты
  - Тех. операции
  - Внутренние заказы
+ Комплект не может быть позицией отгрузки по комиссионному договору:
  - нельзя добавить комплект в отгрузку по комиссионному договору
  - нельзя установить комиссионный договор в отгрузке с комплектами
  - нельзя изменить договор на комиссионный, если по нему есть отгрузки с комплектами


#### Атрибуты вложенных сущностей
##### Метаданные Комплектов
Метаданные Комплектов содержат информацию о дополнительных полях.

Посмотреть все созданные в основном интерфейсе доп. поля Комплектов,
а также все типы цен можно с помощью запроса на получение метаданных Комплектов.
Ответ - объект, со следующей структурой:

+ **meta** - Метаданные
+ **attributes** - коллекция всех существующих доп. полей Комплектов в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

Структуры объектов отдельных коллекций:

##### Штрих коды:
При создании штрихкода требуется описать объект с полем, являющимся форматом представления штрихкода в нижнем регистре, со строковым значением самого штрихкода. Наименование полей отдельного объекта, представляющего штрихкод:

+ **ean13** - штрихкод в формате EAN13, если требуется создать штрихкод в формате EAN13
+ **ean8** - штрихкод в формате EAN8, если требуется создать штрихкод в формате EAN8
+ **code128** - штрихкод в формате Code128, если требуется создать штрихкод в формате Code128
+ **gtin** - штрихкод в формате GTIN, если требуется создать штрихкод в формате GTIN

##### Изображение: структура и загрузка.
При запросе Комплекта с изображениями будет выведено json представление этого Комплекта, содержащее поле **images**. Данное поле является 
массивом элементов. Элементы поля **images** имеют поля:

+ **meta** - Метаданные об изображении
+ **title** - Название изображения
+ **filename** - Имя файла
+ **size** - Размер файла в байтах
+ **updated** - Дата последнего изменения
+ **download** - Ссылка на скачивание изображения в формате Метаданных
+ **miniature** - Ссылка на миниатюру изображения в формате Метаданных
+ **tiny** - Ссылка на уменьшенное изображение в формате Метаданных

<h4>Загрузка</h4>
Для загрузки изображения нужно в теле запроса на [создание](../dictionaries/#suschnosti-komplekt-sozdat-komplekt) или [обновление](../dictionaries/#suschnosti-komplekt-izmenit-komplekt) Комплекта
указать поле **images**  со списком элементов, имеющих следующие атрибуты:

+ **filename** - имя файла с расширением. Например - "банан.png"
+ **content** - Изображение, закодированное в формате Base64.

Если в запросе на обновление **images** будет содержать пустой массив элементов, то все Изображения у Комплекта будут удалены, 
т.к. сервер посчитает, что пользователь хочет обновить список Изображений Комплекта.

Документация API по работе с Изображениями приведена в главе [Изображение](../dictionaries/#suschnosti-izobrazhenie).

О работе с доп. полями Комплектов можно прочитать [здесь](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)

### Получить список комплектов
Запрос на получение всех комплектов для данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

- **meta** [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о выдаче,
- **context** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой комплекты.

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|limit |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|offset |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить список комплектов

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка комплектов.

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
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
    "type": "bundle",
    "mediaType": "application/json",
    "size": 1,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
        "type": "bundle",
        "mediaType": "application/json"
      },
      "id": "c21646cf-ee08-11e6-8af5-581e00000023",
      "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
      "owner": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": true,
      "group": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "updated": "2017-02-08 17:13:26",
      "name": "Комплект с товаром и услугой",
      "code": "00003",
      "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
      "archived": false,
      "pathName": "",
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "images": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
          "type": "images",
          "mediaType": "application/json",
          "size": 0,
          "limit": 1000,
          "offset": 0
        }
      },      
      "minPrice": {
        "value": 500,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "salePrices": [
        {
          "value": 0,
          "currency": {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
              "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
            "name": "Цена продажи",
            "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
          }
        }
      ],
      "weight": 0,
      "volume": 0,
      "trackingType": "NOT_TRACKED",
      "barcodes": [
        {
          "ean13": "2000000000039"
        }
      ],
      "components": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
          "type": "bundlecomponent",
          "mediaType": "application/json",
          "size": 2,
          "limit": 1000,
          "offset": 0
        }
      }
    }
  ],
  "taxSystem": "GENERAL_TAX_SYSTEM"
}
```

### Создать Комплект

Создать новый комплект.

#### Описание

Комплект создается на основе переданного объекта JSON,
который содержит представление нового Комплекта.
Результат - JSON представление созданного Комплекта. Для создания нового Комплекта
необходимо и достаточно указать в переданном объекте не пустое поле `name` и не пустое множество компонентов `components`.
Максимальное число компонентов в Комплекте - 50.

> Пример наиболее полного по количеству полей запроса.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/bundle"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Комплект с товаром и еще одним товаром",
            "code": "00003",
            "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
            "archived": false,
            "pathName": "",
            "discountProhibited": false,
            "uom": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "minPrice": {
              "value": 500,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 20,
                "currency": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  },
                  "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                  "name": "Цена продажи",
                  "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
                }
              }
            ],
            "weight": 0,
            "volume": 0,
            "trackingType": "NOT_TRACKED",
            "barcodes": [
              {
                "ean8": "20000000"
              },
              {
                "ean13": "2000000000000"
              },
              {
                "code128": "code128 barcode"
              },
              {
                "gtin": "00000000000130"
              }
            ],
            "components": [
              {
                "assortment": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                    "type": "product",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 1
              },
              {
                "assortment": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
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
Успешный запрос. Результат - JSON представление созданного Комплекта.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
    "type": "bundle",
    "mediaType": "application/json"
  },
  "id": "c21646cf-ee08-11e6-8af5-581e00000023",
  "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2017-02-08 17:13:26",
  "name": "Комплект с товаром и еще одним товаром",
  "code": "00003",
  "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
  "archived": false,
  "pathName": "",
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
      "type": "image",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },  
  "minPrice": {
    "value": 500,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "salePrices": [
    {
      "value": 20,
      "currency": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
        "name": "Цена продажи",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
      }
    }
  ],
  "weight": 0,
  "volume": 0,
  "trackingType": "NOT_TRACKED",
  "barcodes": [
    {
      "ean8": "20000000"
    },
    {
      "ean13": "2000000000000"
    },
    {
      "code128": "code128 barcode"
    },
    {
      "gtin": "00000000000130"
    }
  ],
  "components": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
      "type": "bundlecomponent",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    },
    "rows": [
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      },
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000d",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000d",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      }
    ]
  }
}
```

> Пример запроса на создание Комплекта с загрузкой изображения

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/bundle"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Комплект с изображением",
            "images": [
              {
                "filename": "birdimages.png",
                "content": "base64"
              }
            ],
            "components": [
              {
                "assortment": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
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
Успешный запрос. Результат - JSON представление созданного Комплекта.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
    "type": "bundle",
    "mediaType": "application/json"
  },
  "id": "c21646cf-ee08-11e6-8af5-581e00000023",
  "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2017-02-08 17:13:26",
  "name": "Комплект с картинкой",
  "code": "00003",
  "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
  "archived": false,
  "pathName": "",
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
      "type": "images",
      "mediaType": "application/json",
      "size": 1,
      "limit": 1000,
      "offset": 0
    },
    "updated": "2017-01-11 14:54:10",
    "title": "birdimages.png",
    "filename": "birdimages.png",
    "size": 14052,
    "miniature": {
      "href": "https://online.moysklad.ru/api/remap/1.3/download/bd159783-95ee-11e6-8a84-bae500000001?miniature=true",
      "mediaType": "images/png"
    },
    "tiny": {
      "href": "https://online.moysklad.ru/app/download/bd14f0b6-95ee-11e6-8a84-bae500000000.png",
      "mediaType": "images/png"
    }
  },  
  "minPrice": {
    "value": 500,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "salePrices": [
    {
      "value": 20,
      "currency": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
        "name": "Цена продажи",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
      }
    }
  ],
  "weight": 0,
  "volume": 0,
  "trackingType": "NOT_TRACKED",
  "barcodes": [
    {
      "ean13": "2000000000039"
    }
  ],
  "components": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
      "type": "bundlecomponent",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    },
    "rows": [
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      },
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000d",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000d",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      }
    ]
  }
}
```

### Массовое создание и обновление Комплектов
[Массовое создание и обновление](../#mojsklad-json-api-obschie-swedeniq-sozdanie-i-obnowlenie-neskol-kih-ob-ektow) Комплектов.
В теле запроса нужно передать массив, содержащий JSON представления Комплектов, которые вы хотите создать или обновить.
Обновляемые Комплекты должны содержать идентификатор в виде метаданных.

> Пример создания и обновления нескольких Комплектов

  ```shell
    curl -X POST
      "https://online.moysklad.ru/api/remap/1.3/entity/bundle"
      -H "Authorization: Basic <Credentials>"
      -H "Content-Type: application/json"
        -d '[
              {
                "name": "Комплект с товаром и еще одним товаром",
                "code": "00003",
                "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
                "archived": false,
                "pathName": "",
                "uom": {
                  "meta": {
                    "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                    "type": "uom",
                    "mediaType": "application/json"
                  }
                },
                "minPrice": {
                  "value": 500,
                  "currency": {
                    "meta": {
                      "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
                      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                      "type": "currency",
                      "mediaType": "application/json"
                    }
                  }
                },
                "salePrices": [
                  {
                    "value": 20,
                    "currency": {
                      "meta": {
                        "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
                        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                        "type": "currency",
                        "mediaType": "application/json"
                      }
                    },
                    "priceType": {
                      "meta": {
                        "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                        "type": "pricetype",
                        "mediaType": "application/json"
                      },
                      "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                      "name": "Цена продажи",
                      "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
                    }
                  }
                ],
                "weight": 0,
                "volume": 0,
                "trackingType": "NOT_TRACKED",
                "barcodes": [
                  {
                    "ean8": "20000000"
                  },
                  {
                    "ean13": "2000000000000"
                  },
                  {
                    "code128": "code128 barcode"
                  },
                  {
                    "gtin": "00000000000130"
                  }
                ],
                "components": [
                  {
                    "assortment": {
                      "meta": {
                        "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
                        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                        "type": "product",
                        "mediaType": "application/json"
                      }
                    },
                    "quantity": 1
                  },
                  {
                    "assortment": {
                      "meta": {
                        "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
                        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                        "type": "product",
                        "mediaType": "application/json"
                      }
                    },
                    "quantity": 1
                  }
                ]
              },
              {
                "meta": {
                  "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
                  "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
                  "type": "bundle",
                  "mediaType": "application/json"
                },
                "name": "Новое наименование",
                "barcodes": [
                  {
                    "ean8": "20000000"
                  },
                  {
                    "ean13": "2000000000000"
                  },
                  {
                    "code128": "code128 barcode"
                  },
                  {
                    "gtin": "00000000000130"
                  }
                ]
              }
            ]'  
  ```
> Response 200 (application/json)
Успешный запрос. Результат - массив JSON представлений созданных и обновленных Комплектов.
  
  ```json
  [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
        "type": "bundle",
        "mediaType": "application/json"
      },
      "id": "c21646cf-ee08-11e6-8af5-581e00000023",
      "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
      "owner": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": true,
      "group": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "updated": "2017-02-08 17:13:26",
      "name": "Комплект с товаром и еще одним товаром",
      "code": "00003",
      "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
      "archived": false,
      "pathName": "",
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "images": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
            "type": "images",
            "mediaType": "application/json",
            "size": 0,
            "limit": 1000,
            "offset": 0
          }
      },  
      "minPrice": {
        "value": 500,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "salePrices": [
        {
          "value": 20,
          "currency": {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
              "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
            "name": "Цена продажи",
            "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
          }
        }
      ],
      "weight": 0,
      "volume": 0,
      "trackingType": "NOT_TRACKED",
      "barcodes": [
        {
          "ean8": "20000000"
        },
        {
          "ean13": "2000000000000"
        },
        {
          "code128": "code128 barcode"
        },
        {
          "gtin": "00000000000130"
        }
      ],
      "components": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
          "type": "bundlecomponent",
          "mediaType": "application/json",
          "size": 2,
          "limit": 1000,
          "offset": 0
        },
        "rows": [
          {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
              "type": "bundlecomponent",
              "mediaType": "application/json"
            },
            "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
            "accountId": "903083d9-d973-11e6-5bed-427b00000001",
            "assortment": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              }
            },
            "quantity": 1
          },
          {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000d",
              "type": "bundlecomponent",
              "mediaType": "application/json"
            },
            "id": "9404273f-eeb6-11e6-5bed-427b0000000d",
            "accountId": "903083d9-d973-11e6-5bed-427b00000001",
            "assortment": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              }
            },
            "quantity": 1
          }
        ]
      }
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
        "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
        "type": "bundle",
        "mediaType": "application/json"
      },
      "id": "c21646cf-ee08-11e6-8af5-581e00000023",
      "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
      "owner": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": true,
      "group": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "updated": "2017-02-08 17:13:26",
      "name": "Новое наименование",
      "code": "00003",
      "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
      "archived": false,
      "pathName": "",
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
     "images": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
          "type": "images",
          "mediaType": "application/json",
          "size": 0,
          "limit": 1000,
          "offset": 0
        }
      },      
      "minPrice": {
        "value": 500,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "salePrices": [
        {
          "value": 20,
          "currency": {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
              "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
            "name": "Цена продажи",
            "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
          }
        }
      ],
      "weight": 0,
      "volume": 0,
      "trackingType": "NOT_TRACKED",
      "barcodes": [
        {
          "ean8": "20000000"
        },
        {
          "ean13": "2000000000000"
        },
        {
          "code128": "code128 barcode"
        },
        {
          "gtin": "00000000000130"
        }
      ],
      "components": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
          "type": "bundlecomponent",
          "mediaType": "application/json",
          "size": 2,
          "limit": 1000,
          "offset": 0
        },
        "rows": [
          {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
              "type": "bundlecomponent",
              "mediaType": "application/json"
            },
            "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
            "accountId": "903083d9-d973-11e6-5bed-427b00000001",
            "assortment": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              }
            },
            "quantity": 1
          },
          {
            "meta": {
              "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000d",
              "type": "bundlecomponent",
              "mediaType": "application/json"
            },
            "id": "9404273f-eeb6-11e6-5bed-427b0000000d",
            "accountId": "903083d9-d973-11e6-5bed-427b00000001",
            "assortment": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              }
            },
            "quantity": 1
          }
        ]
      }
    }
  ]
  ```
  
### Метаданные Комплектов
#### Метаданные Комплектов
Запрос на получение метаданных Комплектов. Результат - объект JSON, включающий в себя:

+ **meta** - Метаданные
+ **attributes** - коллекция всех существующих доп. полей Комплектов в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

Структура отдельного объекта, представляющего доп. поле подробно описана в разделе [Работа с дополнительными полями](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi).

> Получить метаданные комплектов

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление доп. полей Комплектов.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle",
    "mediaType": "application/json"
  },
  "attributes": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata/attributes/5a374c72-ee21-11e6-8af5-581e00000003",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "5a374c72-ee21-11e6-8af5-581e00000003",
      "name": "доп строка",
      "type": "string",
      "required": false
    }
  ]
}
```

### Отдельное доп. поле

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Доп. поля.|

#### Отдельное доп. поле

> Запрос на получение информации по отдельному дополнительному полю.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata/attributes/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного доп. поля.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata/attributes/5a374c72-ee21-11e6-8af5-581e00000003",
    "type": "attributemetadata",
    "mediaType": "application/json"
  },
  "id": "5a374c72-ee21-11e6-8af5-581e00000003",
  "name": "доп строка",
  "type": "string",
  "required": false
}
```

### Комплект

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|

### Получить Комплект

> Запрос на получение комплекта с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление комплекта.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
    "type": "bundle",
    "mediaType": "application/json"
  },
  "id": "c21646cf-ee08-11e6-8af5-581e00000023",
  "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2017-02-08 17:13:26",
  "name": "Комплект с товаром и услугой",
  "code": "00003",
  "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
  "archived": false,
  "pathName": "",
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
      "type": "images",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },  
  "minPrice": {
    "value": 500,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "salePrices": [
    {
      "value": 0,
      "currency": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
        "name": "Цена продажи",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
      }
    }
  ],
  "weight": 0,
  "volume": 0,
  "trackingType": "NOT_TRACKED",
  "barcodes": [
    {
      "ean13": "2000000000039"
    }
  ],
  "components": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
      "type": "bundlecomponent",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    }
  }
}
```

### Изменить Комплект

Запрос на обновление существующего Комплекта.
Типы цен в ценах продаж, дополнительные поля и компоненты обновляются как элементы вложенных коллекций:

+ Если в текущем объекте у какого-то из доп. полей / типов цен / компонентов нет значения,
а в переданной коллекции оно есть - значение записывается в доп. поле / тип цены / компонент.
+ Если же у данного атрибута значение уже присутствует - оно перезаписывается на переданное.
+ Если у данного атрибута в составе объекта значение присутствует, однако оно отсутствует
в передаваемой в теле запроса коллекции (не передается совсем), то значение атрибута объекта не изменяется.

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|

> Пример запроса на обновление Комплекта
 
 ```shell
   curl -X PUT
     "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19"
     -H "Authorization: Basic <Credentials>"
     -H "Content-Type: application/json"
       -d '{
             "name": "Новое наименование",
             "barcodes": [
               {
                 "ean8": "20000000"
               },
               {
                 "ean13": "2000000000000"
               },
               {
                 "code128": "code128 barcode"
               },
               {
                 "gtin": "00000000000130"
               }
             ],
           }'  
 ```
 
>  Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Комплекта.
 
 ```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023",
    "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
    "type": "bundle",
    "mediaType": "application/json"
  },
  "id": "c21646cf-ee08-11e6-8af5-581e00000023",
  "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
  "owner": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/employee/bb430a4e-ee05-11e6-8af5-581e0000002a",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/group/bade121f-ee05-11e6-8af5-581e00000002",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2017-02-08 17:13:26",
  "name": "Новое наименование",
  "code": "00003",
  "externalCode": "iOzqxcTCiAK1-6-eAjVR12",
  "archived": false,
  "pathName": "",
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/images",
      "type": "images",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },  
  "minPrice": {
    "value": 500,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/10772c12-36e7-11e7-8a7f-40d000000097",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "salePrices": [
    {
      "value": 20,
      "currency": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/currency/bb724075-ee05-11e6-8af5-581e00000058",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
        "name": "Цена продажи",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f43529a"
      }
    }
  ],
  "weight": 0,
  "volume": 0,
  "trackingType": "NOT_TRACKED",
  "barcodes": [
    {
      "ean8": "20000000"
    },
    {
      "ean13": "2000000000000"
    },
    {
      "code128": "code128 barcode"
    },
    {
      "gtin": "00000000000130"
    }
  ],
  "components": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
      "type": "bundlecomponent",
      "mediaType": "application/json",
      "size": 2,
      "limit": 1000,
      "offset": 0
    },
    "rows": [
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      },
      {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000d",
          "type": "bundlecomponent",
          "mediaType": "application/json"
        },
        "id": "9404273f-eeb6-11e6-5bed-427b0000000d",
        "accountId": "903083d9-d973-11e6-5bed-427b00000001",
        "assortment": {
          "meta": {
            "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b9",
            "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
          }
        },
        "quantity": 1
      }
    ]
  }
} 
 ``` 
  
### Удалить Комплект

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|

> Запрос на удаление Комплекта с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление Комплекта.

### Массовое удаление Комплектов

В теле запроса нужно передать массив, содержащий JSON метаданных Комплектов, которые вы хотите удалить.


> Запрос на массовое удаление Комплектов. 

```shell
curl -X POST
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/delete"
  -H "Authorization: Basic <Credentials>"
  -H "Content-Type: application/json"
  -d '[
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b1",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
            "type": "bundle",
            "mediaType": "application/json"
        },
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b2",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/bundle/metadata",
            "type": "bundle",
            "mediaType": "application/json"
        }
      ]'
```        

> Успешный запрос. Результат - JSON информация об удалении Комплектов.

```json
[
  {
    "info":"Сущность 'bundle' с UUID: 7944ef04-f831-11e5-7a69-971500188b1 успешно удалена"
  },
  {
    "info":"Сущность 'bundle' с UUID: 7944ef04-f831-11e5-7a69-971500188b2 успешно удалена"
  }
]
```  

### Компоненты Комплекта

Отдельный ресурс для управления компонентами Комплекта.

### Получить компоненты Комплекта
Запрос на получение списка всех компонентов данного Комплекта.

- **meta** [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о выдаче,
- **context** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой компоненты Комплекта.

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|
|limit |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|offset |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить компоненты Комплекса

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19/components"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка компонентов отдельного Комплекта.

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
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components",
    "type": "bundlecomponent",
    "mediaType": "application/json",
    "size": 2,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/c21661f2-ee08-11e6-8af5-581e00000026",
        "type": "bundlecomponent",
        "mediaType": "application/json"
      },
      "id": "c21661f2-ee08-11e6-8af5-581e00000026",
      "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
      "assortment": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/service/b3d8d132-ee08-11e6-8af5-581e00000013",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/service/metadata",
          "type": "service",
          "mediaType": "application/json"
        }
      },
      "quantity": 1
    },
    {
      "meta": {
        "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/c21668eb-ee08-11e6-8af5-581e00000027",
        "type": "bundlecomponent",
        "mediaType": "application/json"
      },
      "id": "c21668eb-ee08-11e6-8af5-581e00000027",
      "accountId": "badae4a0-ee05-11e6-8af5-581e00000001",
      "assortment": {
        "meta": {
          "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/b01e8dfd-ee08-11e6-8af5-581e00000005",
          "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
          "type": "product",
          "mediaType": "application/json"
        }
      },
      "quantity": 1
    }
  ]
}
```

### Добавить компонент Комплекта

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|

> Запрос на добавление компонента Комплекта.

```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19/components"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "assortment": {
              "meta": {
                "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
                "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              }
            },
            "quantity": 1
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление добавленного компонента.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
    "type": "bundlecomponent",
    "mediaType": "application/json"
  },
  "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
  "accountId": "903083d9-d973-11e6-5bed-427b00000001",
  "assortment": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json"
    }
  },
  "quantity": 1
}
```


### Компонент Комплекта

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|
|id |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id компонента Комплекта.|

### Получить компонент

> Запрос на получение отдельного компонента Комплекта с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19/components/34f6344f-015e-11e6-9464-e4de0000006c"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного компонента Комплекта.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
    "type": "bundlecomponent",
    "mediaType": "application/json"
  },
  "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
  "accountId": "903083d9-d973-11e6-5bed-427b00000001",
  "assortment": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json"
    }
  },
  "quantity": 1
}
```

### Обновить компонент

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|
|id |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id компонента Комплекта.|

Запрос на обновление отдельного компонента Комплекта с указанным id.

> Пример запроса на обновление компонента Комплекта

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19/components/34f6344f-015e-11e6-9464-e4de0000006c
"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "quantity": 50
          }'  
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного компонента Комплекта.

```json
{
  "meta": {
    "href": "http://online.moysklad.ru/api/remap/1.3/entity/bundle/c21646cf-ee08-11e6-8af5-581e00000023/components/9404273f-eeb6-11e6-5bed-427b0000000c",
    "type": "bundlecomponent",
    "mediaType": "application/json"
  },
  "id": "9404273f-eeb6-11e6-5bed-427b0000000c",
  "accountId": "903083d9-d973-11e6-5bed-427b00000001",
  "assortment": {
    "meta": {
      "href": "http://online.moysklad.ru/api/remap/1.3/entity/product/010afdea-ea40-11e6-5bed-427b000000b8",
      "metadataHref": "http://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json"
    }
  },
  "quantity": 50
}
```

### Удалить компонент

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Комплекта.|
|id |  `string` (required) *Example: 34f6344f-015e-11e6-9464-e4de0000006c* id компонента Комплекта.|

> Запрос на удаление отдельного компонента Комплекта с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/bundle/7944ef04-f831-11e5-7a69-971500188b19/components/34f6344f-015e-11e6-9464-e4de0000006c"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление компонента Комплекта.
