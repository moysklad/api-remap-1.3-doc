## Товар
### Товары 
Средствами JSON API можно создавать и обновлять сведения о Товарах, запрашивать списки Товаров и сведения по отдельным Товарам.
 Кодом сущности для Товара в составе JSON API является ключевое слово **product**. Больше о Товарах и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки в разделе
 [Товары и склад](https://support.moysklad.ru/hc/ru/sections/200564973-%D0%A2%D0%BE%D0%B2%D0%B0%D1%80%D1%8B-%D0%B8-%D1%81%D0%BA%D0%BB%D0%B0%D0%B4).
По данной сущности можно осуществлять контекстный поиск с помощью специального параметра `search`. Подробнее можно узнать по [ссылке](../#mojsklad-json-api-obschie-swedeniq-kontextnyj-poisk).

Поиск среди объектов товаров на соответствие поисковой строке будет осуществлен по следующим полям:

+ по наименованию товара (name)
+ по коду товара (code)
+ по артикулу (article)

#### Атрибуты сущности
+ **meta** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) объекта
+ **id** - ID Товара в формате UUID `Только для чтения`
+ **accountId** - ID учетной записи `Только для чтения`
+ **owner** - Ссылка на Владельца (Сотрудника) в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **shared** - Общий доступ
+ **group** - Отдел сотрудника в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **syncId** - ID синхронизации. После заполнения недоступен для изменения.
+ **updated** - Момент последнего обновления сущности `Только для чтения`
+ **name** - Наименование Товара `Необходимое`
+ **description** - Описание Товара
+ **code** - Код Товара
+ **externalCode** - Внешний код Товара
+ **archived** - Отметка о том, добавлен ли Товар в архив
+ **pathName** - Наименование группы, в которую входит Товар `Только для чтения`
+ **vat** - НДС %
+ **effectiveVat** - Реальный НДС % `Только для чтения`
+ **productFolder** - Ссылка на группу Товаров в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **uom** - Ссылка на единицы измерения в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **images** - Изображения Товара. Изображений у Товара может быть не более 10
+ **minPrice** - Минимальная цена
+ **buyPrice** - Закупочная цена
+ **salePrices** - Цены продажи
+ **supplier** - Ссылка на контрагента-поставщика в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **attributes** - Коллекция доп. полей в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **country** - Ссылка на страну в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **article** - Артикул
+ **weighed** - Весовой товар
+ **tobacco** - Табачная продукция. Не может быть указан вместе с **alcoholic**, **weighed** и **isSerialTrackable**
+ **weight** - Вес
+ **volume** - Объем
+ **packs** - Упаковки Товара
+ **barcodes** - Массив штрихкодов товара
+ **discountProhibited** - Признак запрета скидок.
+ **alcoholic** - Объект, содержащий поля алкогольной продукции.
  + **excise** - Содержит акцизную марку
  + **type**  - Код вида продукции
  + **strength** - Крепость
  + **volume** - Объём тары
+ **variantsCount** - Количество модификаций у данного товара `Только для чтения`
+ **minimumBalance** - Неснижаемый остаток
+ **isSerialTrackable** - Учет по серийным номерам. Не может быть указан вместе с **alcoholic** и **weighed**
+ **things** - Серийные номера `Только для чтения`
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
+ **personalProtectiveItemType** - Код вида номенклатурной классификации медицинских средств индивидуальной защиты (EAN-13)
  + **2400001323807** - маска лицевая для защиты дыхательных путей, многоразового использования            
  + **2400003675805** - маска лицевая для защиты дыхательных путей, одноразового использования             
  + **2400001807703** - респиратор общего применения	                                                     
  + **2400001818303** - респиратор хирургический                                                           
  + **2400002186203** - респиратор хирургический антибактериальный	                                     
  + **2400001368105** - средство назальное для защиты от загрязненного воздуха, местного действия          
  + **2400001225408** - перчатки смотровые (процедурные) из латекса гевеи, неопудренные, нестерильные      
  + **2400001225606** - перчатки смотровые (процедурные) из латекса гевеи, опудренные                      
  + **2400001226108** - перчатки смотровые (процедурные) из латекса гевеи, неопудренные, стерильные	     
  + **2400001393503** - перчатки смотровые (процедурные) из полихлоропрена, неопудренные                   
  + **2400001858309** - перчатки смотровые (процедурные) нитриловые, неопудренные, нестерильные	         
  + **2400001858507** - перчатки смотровые (процедурные) нитриловые, опудренные	                         
  + **2400002052805** - перчатки смотровые (процедурные) виниловые, неопудренные                           
  + **2400002052904** - перчатки смотровые (процедурные) виниловые, опудренные	                         
  + **2400002984502** - перчатки смотровые (процедурные) из гваюлового латекса, неопудренные	             
  + **2400003117107** - перчатки смотровые (процедурные) из этиленвинилацетата, неопудренные, стерильные   
  + **2400003117206** - перчатки смотровые (процедурные) из этиленвинилацетата, неопудренные, нестерильные 
  + **2400003207907** - перчатки смотровые (процедурные) нитриловые, неопудренные, антибактериальные	     
  + **2400003215308** - перчатки смотровые (процедурные) полиизопреновые, неопудренные	                 
  + **2400003297700** - перчатки смотровые (процедурные) нитриловые, неопудренные, стерильные	             
  + **2400003356704** - перчатки смотровые (процедурные) виниловые, неопудренные, стерильные	             
  + **2400003356803** - перчатки смотровые (процедурные) виниловые, опудренные, стерильные	             
  + **2400003433108** - перчатки смотровые (процедурные) из латекса гевеи, опудренные, стерильные	         
  + **2400003492303** - перчатки смотровые (процедурные) полиизопреновые, опудренные	                     
  + **2400003495700** - перчатки смотровые (процедурные) из полихлоропрена, неопудренные, стерильные	     
  + **2400003495809** - перчатки смотровые (процедурные) из полихлоропрена, неопудренные, стерильные	     
  + **2400003495908** - перчатки смотровые (процедурные) нитриловые, опудренные, стерильные	             
  + **2400003496004** - перчатки смотровые (процедурные) полиизопреновые, неопудренные, стерильные	     
  + **2400003496103** - перчатки смотровые (процедурные) полиизопреновые, опудренные, стерильные	         
  + **2400001226306** - перчатки хирургические из латекса гевеи, неопудренные	                             
  + **2400001226405** - перчатки хирургические из латекса гевеи, опудренные	                             
  + **2400001393107** - перчатки хирургические из полихлоропрена, неопудренные	                         
  + **2400001393602** - перчатки смотровые (процедурные) из полихлоропрена, опудренные	                 
  + **2400001565306** - перчатки хирургические из блоксополимера стирола, неопудренные, антибактериальные	 
  + **2400001857203** - перчатки хирургические нитриловые, опудренные	                                     
  + **2400001857005** - перчатки хирургические нитриловые, неопудренные	                                 
  + **2400002015909** - перчатки хирургические полиизопреновые, неопудренные	                             
  + **2400002016005** - перчатки хирургические полиизопреновые, неопудренные, антибактериальные            
  + **2400002016104** - перчатки хирургические полиизопреновые, опудренные	                             
  + **2400003161209** - перчатки хирургические из блоксополимера стирола, неопудренные	                 
  + **2400003227806** - перчатки хирургические полимерно-композитные, неопудренные	                     
  + **2400003237409** - перчатки хирургические полимерно-композитные, неопудренные	                     
  + **2400003263408** - перчатки хирургические из латекса гевеи, неопудренные, антибактериальные	         
  + **2400003356902** - перчатки хирургические из гваюлового латекса, неопудренные	                     
  + **2400003356902** - перчатки хирургические из полихлоропрена, опудренные	                             
  + **2400002886806** - набор гигиенической одежды для посетителей	                                     
  + **2400002886707** - комбинезон гигиенический для посетителей

Атрибут **pathName** сам по себе является атрибутом только для чтения, однако его можно изменить
с помощью обновления атрибута **productFolder**.

#### Атрибуты вложенных сущностей
##### Упаковки Товара:
+ **id** - ID в формате UUID `Только для чтения`
+ **uom** - Ссылка на единицы измерения в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye) `Необходимое`
+ **quantity** - Количество Товаров в упаковке данного вида `Необходимое`
+ **barcodes** - Массив штрихкодов упаковок товаров. Данный массив может содержать не более одного штрихкода. Если штрихкод в массиве отсутствует, то данное поле не выводится.
В версии API 1.3 был удален отдельный ресурс для работы с упаковками товаров. Теперь упаковки - вложенная коллекция.
Для того, чтобы создать новую упаковку для данного товара, нужно в запросе на обновление товара указать ее как элемент
поля **packs**, а в ее составе указать ссылку в формате meta на единицу измерения и количество товаров в упаковке.
Для упаковки товара нельзя указать ссылку на единицу измерения, совпадающую с единицей измерения товара, иначе возникнет ошибка.
При обновлении штрихкодов упаковки в рамках обновления товара, переданная коллекция штрихкодов упаковки полностью заменяет имеющуюся до этого 
коллекцию.
Для обновления списка упаковок товара, необходимо в рамках обновления товара передать новую коллекцию упаковок. Новая коллекия упаковок товара
 полностью заменит старую коллекцию.

##### Метаданные Товаров
Метаданные Товаров содержат информацию о дополнительных полях.

Посмотреть все созданные в основном интерфейсе доп. поля Товаров,
а также все типы цен можно с помощью запроса на получение метаданных Товаров.
Ответ - объект, со следующей структурой:

+ **meta** - Метаданные
+ **attributes** - коллекция всех существующих доп. полей Товаров в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **createShared** - создавать новые Товары с меткой "Общий"

Структуры объектов отдельных коллекций:

##### Штрих коды:
При создании штрихкода требуется описать объект с полем, являющимся форматом представления штрихкода в нижнем регистре, со строковым значением самого штрихкода. Наименование полей отдельного объекта, представляющего штрихкод:

+ **ean13** - штрихкод в формате EAN13, если требуется создать штрихкод в формате EAN13
+ **ean8** - штрихкод в формате EAN8, если требуется создать штрихкод в формате EAN8
+ **code128** - штрихкод в формате Code128, если требуется создать штрихкод в формате Code128
+ **gtin** - штрихкод в формате GTIN, если требуется создать штрихкод в формате GTIN

О работе с доп. полями Товаров можно прочитать [здесь](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi)

##### Поставщик Товара:
+ **meta** - Метаданные, содержащие ссылку на поставщика.
Тип поставщика - Контрагент. Описание сущности Контрагент вы можете посмотреть [здесь](../dictionaries/#suschnosti-kontragent)

##### Цены продажи
+ **value** - Значение цены
+ **currency** - Ссылка на валюту в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)
+ **priceType** - Тип цены


##### Закупочная цена
+ **value** - Значение цены
+ **currency** - Ссылка на валюту в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

##### Минимальная цена
+ **value** - Значение цены
+ **currency** - Ссылка на валюту в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)

##### Изображение: структура и загрузка.
При запросе Товара с изображениями будет выведено json представление этого Товара, содержащее поле **images**. Данное поле является 
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
Для загрузки изображений нужно в теле запроса на [создание](../dictionaries/#suschnosti-towar-sozdat-towar) или [обновление](../dictionaries/#suschnosti-towar-izmenit-towar) товара
указать поле **images** со списком элементов, имеющих следующие атрибуты:

+ **filename** - имя файла с расширением. Например - "банан.png"
+ **content** - Изображение, закодированное в формате Base64.

Если в запросе на обновление **images** будет содержать пустой массив элементов, то все Изображения у Товара будут удалены, 
т.к. сервер посчитает, что пользователь хочет обновить список Изображений Товара.

Документация API по работе с Изображениями приведена в главе [Изображение](../dictionaries/#suschnosti-izobrazhenie).

##### Группа Товара
+ **meta** - Метаданные, содержащие ссылку на группу Товара.
Описание сущности Группа вы можете посмотреть [здесь](../dictionaries/#suschnosti-gruppa-towarow)
Обновление этого атрибута также обновит атрибут **pathName**.

##### Весовой товар
+ **weighed** - Поле, показывающее является ли товар весовым. Если его значение false - поле не отображается.
Если в основном интерфейсе у товара стоит отметка об учете его по серийным номерам, выставить значение данного поля на true невозможно.

##### Особенности фильтрации поля archived
Если одновременно осуществляется фильтрация по полям **id** и **archived**, то фильтрация по полю **archived** не учитывается.


### Получить список Товаров 
Запрос на получение всех Товаров для данной учетной записи.
Результат: Объект JSON, включающий в себя поля:

- **meta** [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о выдаче,
- **context** - [Метаданные](../#mojsklad-json-api-obschie-swedeniq-metadannye) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой [Товары](../dictionaries/#suschnosti-towar).

**Параметры**

| Параметр                | Описание  |
| ------------------------------ |:---------------------------|
|limit |  `number` (optional) **Default: 1000** *Example: 1000* Максимальное количество сущностей для извлечения.`Допустимые значения 1 - 1000`.|
|offset |  `number` (optional) **Default: 0** *Example: 40* Отступ в выдаваемом списке сущностей.|

> Получить список Товаров

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка Товаров.
  
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
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json",
    "size": 5,
    "limit": 1000,
    "offset": 0
  },
  "rows": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
        "type": "product",
        "mediaType": "application/json"
      },
      "id": "26b36824-2c83-11e6-8a84-bae50000001b",
      "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
      "updated": "2016-06-07 10:40:48",
      "name": "Тыква",
      "description": "Тыква, Германия",
      "code": "pumpkin1",
      "externalCode": "456pumpkin",
      "archived": false,
      "pathName": "",
      "vat": 18,
      "effectiveVat": 18,
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "images": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
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
          "value": 3353,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
        },
        {
          "value": 3253,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
            "name": "Цена для друзей",
            "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
          }
        }
      ],
      "supplier": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313d1e7-2c7f-11e6-8a84-bae500000051",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
          "type": "counterparty",
          "mediaType": "application/json"
        }
      },
      "attributes": [
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
            "type": "attributemetadata",
            "mediaType": "application/json"
          },
          "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
          "name": "Экспорт",
          "type": "boolean",
          "value": true
        },
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
            "type": "attributemetadata",
            "mediaType": "application/json"
          },
          "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
          "name": "Изготовитель",
          "type": "string",
          "value": "фермерское хозяйство \"Петрович\""
        }
      ],
      "buyPrice": {
        "value": 54,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "article": "Ar23",
      "weight": 200,
      "volume": 300,
      "variantsCount": 0,
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
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/d950551c-2c7f-11e6-8a84-bae50000000b",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
        "type": "product",
        "mediaType": "application/json"
      },
      "id": "d950551c-2c7f-11e6-8a84-bae50000000b",
      "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
      "updated": "2016-06-07 10:45:16",
      "name": "Бананы",
      "description": "Бананы, Африка",
      "code": "one1",
      "externalCode": "456",
      "archived": false,
      "pathName": "",
      "vat": 18,
      "effectiveVat": 18,
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "images": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/d950551c-2c7f-11e6-8a84-bae50000000b/images",
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
          "value": 346347237000,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
        },
        {
          "value": 100,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
            "name": "Цена для друзей",
            "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
          }
        }
      ],
      "supplier": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313d1e7-2c7f-11e6-8a84-bae500000051",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
          "type": "counterparty",
          "mediaType": "application/json"
        }
      },
      "attributes": [
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
            "type": "attributemetadata",
            "mediaType": "application/json"
          },
          "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
          "name": "Экспорт",
          "type": "boolean",
          "value": false
        }
      ],
      "buyPrice": {
        "value": 23553000,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "article": "Ar23",
      "weight": 200,
      "volume": 300,
      "packs": [
        {
          "id": "c6bdee6f-2c83-11e6-8a84-bae5000000a4",
          "uom": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/c6b91d63-2c83-11e6-8a84-bae5000000a1",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
              "type": "uom",
              "mediaType": "application/json"
            }
          },
          "quantity": 35
        },
        {
          "id": "c6bdf693-2c83-11e6-8a84-bae5000000a5",
          "uom": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/c6bc9273-2c83-11e6-8a84-bae5000000a3",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
              "type": "uom",
              "mediaType": "application/json"
            }
          },
          "quantity": 2000
        }
      ],
      "variantsCount": 0,
      "isSerialTrackable": true,
      "things": [
        "F564X056",
        "F564X057"
      ],
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
      "trackingType": "NOT_TRACKED",
      "taxSystem": "GENERAL_TAX_SYSTEM"
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.2/entity/product/26b36824-2c83-11e6-8a84-bae50000031b",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/product/metadata",
        "type": "product",
        "mediaType": "application/json"
      },
      "id": "26b36824-2c83-11e6-8a84-bae50000031b",
      "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
      "owner": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.2/entity/employee/faba7f37-2e58-11e6-8a84-bae500000028",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/employee/metadata",
          "type": "employee",
          "mediaType": "application/json"
        }
      },
      "shared": false,
      "group": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.2/entity/group/f97aa1fb-2e58-11e6-8a84-bae500000002",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/group/metadata",
          "type": "group",
          "mediaType": "application/json"
        }
      },
      "updated": "2016-06-07 10:40:48",
      "name": "Маска",
      "description": "Маска, Гигиеническая",
      "code": "mask1",
      "externalCode": "mask4433",
      "archived": false,
      "pathName": "",
      "vat": 20,
      "effectiveVat": 20,
      "discountProhibited": false,
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.2/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "salePrices": [
        {
          "value": 2600,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.2/entity/currency/6314188d-2c7f-11e6-8a84-bae500000255",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.2/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f23fd",
              "type": "pricetype",
              "mediaType": "application/json"
            },
            "id": "672559f1-cbf3-11e1-9eb9-889ffa6f23fd",
            "name": "Цена продажи",
            "externalCode": "cbcf493b-55bc-11d9-848a-00113333529a"
          }
        }
      ],
      "buyPrice": {
        "value": 12,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.2/entity/currency/6314188d-2c7f-11e6-8a84-bae500002255",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.2/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
      },
      "article": "kk212k",
      "weight": 1,
      "volume": 1,
      "variantsCount": 0,
      "barcodes": [
        {
          "ean13": "2000000000000"
        }
      ],
      "personalProtectiveItemType" : "2400001323807"
    }
  ]
}
```

### Создать Товар 
Создать новый Товар.
#### Описание
Товар создается на основе переданного объекта JSON,
который содержит представление нового Товара.
Результат - JSON представление созданного Товара. Для создания нового Товара,
необходимо и достаточно указать в переданном объекте не пустое поле `name`.
Если вы хотите создать алкогольный товар, то в теле запроса, нужно передать
объект **alcoholic**, у которого как минимум одна из характеристик:

+ **excise** - Содержит акцизную марку
+ **type**  - Код вида продукции
+ **strength** - Крепость
+ **volume** - Объем тары

Будет передана с значением. Иначе, при передаче пустого объекта **alcoholic**,
он будет проигнорирован, и товар создастся без пометки "Алкогольная продукция".

При создании Товара с указанным массивом штрихкодов для каждого штрихкода требуется указать к какому типу относится штрихкод. 
Например, чтобы создать штрихкод с типом Code 128, в массив штрихкодов должен быть добавлен JSON-объект с полем code128 со значением штрихкода.

> Пример наиболее полного по количеству полей запроса.
  
  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Бананы",
            "code": "one1",
            "externalCode": "456",
            "description": "Бананы, Африка",
            "vat": 18,
            "effectiveVat": 18,
            "discountProhibited": false,
            "uom": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "supplier": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/2b5095a4-296b-11e6-8a84-bae500000051",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
                "type": "counterparty",
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
            "buyPrice": {
              "value": 23553000,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 346347237000,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "value": 100,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              }
            ],
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
            "article": "Ar23",
            "weight": 200,
            "volume": 300,
            "packs": [
              {
                "uom": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/2ec1170c-3f69-4409-87bb-c68e0011b275",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                    "type": "uom",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 2
              }
            ],
            "isSerialTrackable": false,
            "trackingType": "NOT_TRACKED"
          }'  
  ```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Товара.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/a355f431-29a1-11e6-8a84-bae500000009",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "a355f431-29a1-11e6-8a84-bae500000009",
  "accountId": "2aa3f5df-296b-11e6-8a84-bae500000001",
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
  "updated": "2016-06-03 18:41:28",
  "name": "Бананы",
  "description": "Бананы, Африка",
  "code": "one1",
  "externalCode": "456",
  "archived": false,
  "pathName": "",
  "vat": 18,
  "effectiveVat": 18,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/a355f431-29a1-11e6-8a84-bae500000009/images",
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
      "value": 346347237000,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 100,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/2b5095a4-296b-11e6-8a84-bae500000051",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "buyPrice": {
    "value": 23553000,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "article": "Ar23",
  "weight": 200,
  "volume": 300,
  "packs": [
    {
      "id": "a97af44b-8b46-11e8-56c0-00080000000d",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/2ec1170c-3f69-4409-87bb-c68e0011b275",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 2
    }
  ],
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

> Пример запроса на создание Товара с единственным необходимым полем.
  
  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Мандарины"
          }'  
  ```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Товара.
  
  ```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/04996e84-29a1-11e6-8a84-bae500000002",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "04996e84-29a1-11e6-8a84-bae500000002",
  "accountId": "2aa3f5df-296b-11e6-8a84-bae500000001",
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
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/04996e84-29a1-11e6-8a84-bae500000002/images",
      "type": "image",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },
  "salePrices": [
    {
      "value": 346347237000,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 100,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "updated": "2016-06-03 18:37:02",
  "name": "Мандарины",
  "code": "00003",
  "externalCode": "Cf0ehavIglre6sMX-J2rR2",
  "archived": false,
  "pathName": "",
  "weight": 0,
  "volume": 0,
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

> Пример запроса на создание Товара с доп. полями.
  
  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Тыква",
            "code": "pumpkin1",
            "externalCode": "456pumpkin",
            "description": "Тыква, Германия",
            "vat": 18,
            "effectiveVat": 18,
            "uom": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "supplier": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313d1e7-2c7f-11e6-8a84-bae500000051",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
                "type": "counterparty",
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
            "buyPrice": {
              "value": 54,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 3353,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "value": 3253,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              }
            ],
            "article": "Ar23",
            "weight": 200,
            "volume": 300,
            "attributes": [
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
                  "type": "attributemetadata",
                  "mediaType": "application/json"
                },
                "name": "Экспорт",
                "value": true
              },
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
                  "type": "attributemetadata",
                  "mediaType": "application/json"
                },
                "name": "Изготовитель",
                "value": "фермерское хозяйство \"Петрович\" "
              },
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0f1e750e-e1b2-11e7-9464-e4de00000003",
                  "type": "attributemetadata",
                  "mediaType": "application/json"
                },
                "name": "not strange attribute name",
                "type": "file",
                "file": {
                  "filename": "filename",
                  "content": "5cYwMpOmNk5kSVr4YgZGKtXJb/7KpHVLDUawyZrD5Nf0WDhB7mS1I77VcAMqYQ8DkP/1wDLhb0X6b2JO4pdpKA=="
                }
              }
            ]
          }'  
  ```
  
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Товара.
 
```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "26b36824-2c83-11e6-8a84-bae50000001b",
  "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
  "updated": "2016-06-07 10:40:48",
  "name": "Тыква",
  "description": "Тыква, Германия",
  "code": "pumpkin1",
  "externalCode": "456pumpkin",
  "archived": false,
  "pathName": "",
  "vat": 18,
  "effectiveVat": 18,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
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
      "value": 3353,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 3253,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313d1e7-2c7f-11e6-8a84-bae500000051",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
      "name": "Экспорт",
      "type": "boolean",
      "value": true
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
      "name": "Изготовитель",
      "type": "string",
      "value": "фермерское хозяйство \"Петрович\""
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0f1e750e-e1b2-11e7-9464-e4de00000003",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0f1e750e-e1b2-11e7-9464-e4de00000003",
      "name": "not strange attribute name",
      "type": "file",
      "value": "filename",
      "download": {
        "href": "https://online.moysklad.ru/api/remap/1.3/download/00664f3a-e3da-11e7-9464-e4de00000000",
        "mediaType": "application/octet-stream"
      }
    }
  ],
  "buyPrice": {
    "value": 54,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "article": "Ar23",
  "weight": 200,
  "volume": 300,
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

> Пример запроса на создание Товара с загрузкой изображения.
  
  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "testimage",
            "images": [
              {
                "filename": "birdimage.png",
                "content": "imageBase64"
              }
            ]
          }'  
  ```
  
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Товара с изображением.
  
  ```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "bd1c0a3e-95ee-11e6-8a84-bae500000004",
  "accountId": "b8b74698-9128-11e6-8a84-bae500000001",
  "owner": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/employee/b905bfb0-9128-11e6-8a84-bae50000002a",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/employee/metadata",
      "type": "employee",
      "mediaType": "application/json"
    }
  },
  "shared": true,
  "group": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/group/b8ba0d3f-9128-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/group/metadata",
      "type": "group",
      "mediaType": "application/json"
    }
  },
  "updated": "2016-10-19 14:25:28",
  "name": "testimage",
  "code": "00006",
  "externalCode": "0bmPIvHxgEDlNIZrZ6GLt2",
  "archived": false,
  "pathName": "",
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images",
      "type": "image",
      "mediaType": "application/json",
      "size": 1,
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
  "buyPrice": {
    "value": 0
  },
  "weight": 0,
  "volume": 0,
  "barcodes": [
    {
      "ean13": "2000000000107"
    }
  ],
  "variantsCount": 0,
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

### Массовое создание и обновление товаров 
[Массовое создание и обновление](../#mojsklad-json-api-obschie-swedeniq-sozdanie-i-obnowlenie-neskol-kih-ob-ektow) товаров.
В теле запроса нужно передать массив, содержащий JSON представления товаров, которые вы хотите создать или обновить.
Обновляемые товары должны содержать идентификатор в виде метаданных.

> Пример создания и обновления нескольких товаров
  
```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product
"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '[
            {
              "name": "Мандарины"
            },
            {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
                "type": "product",
                "mediaType": "application/json"
              },
              "name": "Брюква",
              "description": "Брюква, Брюссель"
            }
          ]'  
  ```

> Response 200 (application/json)
Успешный запрос. Результат - массив JSON представлений созданных и обновленных товаров.

```json
[
  {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/04996e84-29a1-11e6-8a84-bae500000002",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json"
    },
    "id": "04996e84-29a1-11e6-8a84-bae500000002",
    "accountId": "2aa3f5df-296b-11e6-8a84-bae500000001",
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
    
    "salePrices": [
      {
        "value": 346347237000,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
      },
      {
        "value": 100,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/2b50da23-296b-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        },
        "priceType": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
            "type": "pricetype",
            "mediaType": "application/json"
          },
          "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "name": "Цена для друзей",
          "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
        }
      }
    ],
    "updated": "2016-06-03 18:37:02",
    "name": "Мандарины",
    "code": "00003",
    "externalCode": "Cf0ehavIglre6sMX-J2rR2",
    "archived": false,
    "pathName": "",
    "images": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/04996e84-29a1-11e6-8a84-bae500000002/images",
        "type": "image",
        "mediaType": "application/json",
        "size": 0,
        "limit": 1000,
        "offset": 0
      }
    },  
    "weight": 0,
    "volume": 0,
    "isSerialTrackable": false,
    "trackingType": "NOT_TRACKED"
  },
  {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
      "type": "product",
      "mediaType": "application/json"
    },
    "id": "26b36824-2c83-11e6-8a84-bae50000001b",
    "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
    "updated": "2016-06-07 11:00:37",
    "name": "Брюква",
    "description": "Брюква, Брюссель",
    "code": "pumpkin1",
    "externalCode": "456pumpkin",
    "archived": false,
    "pathName": "",
    "vat": 3,
    "effectiveVat": 3,
    "discountProhibited": false,
    "uom": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
        "type": "uom",
        "mediaType": "application/json"
      }
    },
    "images": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
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
        "value": 3753,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
      },
      {
        "value": 3653,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        },
        "priceType": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
            "type": "pricetype",
            "mediaType": "application/json"
          },
          "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "name": "Цена для друзей",
          "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
        }
      }
    ],
    "supplier": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
        "type": "counterparty",
        "mediaType": "application/json"
      }
    },
    "attributes": [
      {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
          "type": "attributemetadata",
          "mediaType": "application/json"
        },
        "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "name": "Экспорт",
        "type": "boolean",
        "value": false
      },
      {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
          "type": "attributemetadata",
          "mediaType": "application/json"
        },
        "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
        "name": "Изготовитель",
        "type": "string",
        "value": "Колхоз \"Иваново\""
      }
    ],
    "country": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/country/0238a888-c602-4e78-a199-d8f49c4d6c18",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/country/metadata",
        "type": "country",
        "mediaType": "application/json"
      }
    },
    "buyPrice": {
      "value": 54,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      }
    },
    "article": "Ar23",
    "weight": 100,
    "volume": 400,
    "packs": [
      {
        "id": "354ba98c-2cb9-11e6-8a84-bae5000000e3",
        "uom": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/2d1fdd55-d935-4d55-80d4-f6904b62ff46",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
            "type": "uom",
            "mediaType": "application/json"
          }
        },
        "quantity": 40
      },
      {
        "id": "354ba98c-2cb9-11e6-8a84-bae5000004e3",
        "uom": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/0dd4fe8b-e59e-486e-bde5-b52fe0e25415",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
            "type": "uom",
            "mediaType": "application/json"
          }
        },
        "quantity": 101
      }
    ],
    "barcodes": [
      {
        "code128": "code128barcode"
      }
    ],
    "alcoholic": {
      "excise": true,
      "type": 3100,
      "strength": 0.6,
      "volume": 1.5
    },
    "isSerialTrackable": false,
    "trackingType": "NOT_TRACKED"
  }
]

```


### Удалить Товар

**Параметры**

|Параметр   | Описание  | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Товара.|
 
> Запрос на удаление Товара с указанным id.

```shell
curl -X DELETE
  "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешное удаление Товара.

### Массовое удаление Товаров

В теле запроса нужно передать массив, содержащий JSON метаданных Товаров, которые вы хотите удалить.


> Запрос на массовое удаление Товаров. 

```shell
curl -X POST
  "https://online.moysklad.ru/api/remap/1.3/entity/product/delete"
  -H "Authorization: Basic <Credentials>"
  -H "Content-Type: application/json"
  -d '[
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b1",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
        },
        {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b2",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
            "type": "product",
            "mediaType": "application/json"
        }
      ]'
```        

> Успешный запрос. Результат - JSON информация об удалении Товаров.

```json
[
  {
    "info":"Сущность 'product' с UUID: 7944ef04-f831-11e5-7a69-971500188b1 успешно удалена"
  },
  {
    "info":"Сущность 'product' с UUID: 7944ef04-f831-11e5-7a69-971500188b2 успешно удалена"
  }
]
```  


### Метаданные Товаров 
#### Метаданные Товаров 
Запрос на получение метаданных Товаров. Результат - объект JSON, включающий в себя:

|   |   | 
|---|---|
|meta   |Метаданные   |
|attributes   |коллекция всех существующих доп. полей Товаров в формате [Метаданных](../#mojsklad-json-api-obschie-swedeniq-metadannye)   |
|createShared   |создавать новые комплекты с меткой "Общий"   |

Структура отдельного объекта, представляющего доп. поле подробно описана в разделе [Работа с дополнительными полями](../#mojsklad-json-api-obschie-swedeniq-rabota-s-dopolnitel-nymi-polqmi).

> Метаданные Товаров

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление доп. полей Товаров.
  
```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product",
    "mediaType": "application/json"
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
      "name": "Экспорт",
      "type": "boolean",
      "required": false
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
      "name": "Изготовитель",
      "type": "string",
      "required": false
    }
  ],
  "createShared": true
}
```

### Отдельное доп. поле

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id   |`7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Доп. поля   |

#### Отдельное доп. поле
> Запрос на получение информации по отдельному дополнительному полю.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного доп. поля.  
  
```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/3cd83619-5585-11e6-8a84-bae500000069",
    "type": "attributemetadata",
    "mediaType": "application/json"
  },
  "customEntityMeta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/metadata/customEntities/a27aa372-5311-11e6-8a84-bae500000001",
    "type": "customentitymetadata",
    "mediaType": "application/json"
  },
  "id": "3cd83619-5585-11e6-8a84-bae500000069",
  "name": "Связанная сущность",
  "type": "customentity",
  "required": false
}
```

### Товар 
Товар, обращение к которому происходит по значению его id.

### Получить Товар

**Параметры**

|Параметр   |Описание   | 
|---|---|
|id |  `string` (required) *Example: 7944ef04-f831-11e5-7a69-971500188b19* id Товара.|

> Запрос на получение Товара с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
Успешный запрос. Результат - JSON представление Товара.

```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/d950551c-2c7f-11e6-8a84-bae50000000b",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "d950551c-2c7f-11e6-8a84-bae50000000b",
  "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
  "updated": "2016-06-07 10:45:16",
  "name": "Бананы",
  "description": "Бананы, Африка",
  "code": "one1",
  "externalCode": "456",
  "archived": false,
  "pathName": "",
  "vat": 18,
  "effectiveVat": 18,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/d950551c-2c7f-11e6-8a84-bae50000000b/images",
      "type": "image",
      "mediaType": "application/json",
      "size": 0,
      "limit": 1000,
      "offset": 0
    }
  },  
  "minPrice": {
    "value": 532000,
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
      "value": 346347237000,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 100,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313d1e7-2c7f-11e6-8a84-bae500000051",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
      "name": "Экспорт",
      "type": "boolean",
      "value": false
    }
  ],
  "buyPrice": {
    "value": 23553000,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "article": "Ar23",
  "weight": 200,
  "volume": 300,
  "packs": [
    {
      "id": "c6bdee6f-2c83-11e6-8a84-bae5000000a4",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/c6b91d63-2c83-11e6-8a84-bae5000000a1",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 35
    },
    {
      "id": "c6bdf693-2c83-11e6-8a84-bae5000000a5",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/c6bc9273-2c83-11e6-8a84-bae5000000a3",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 2000
    }
  ],
  "variantsCount": 0,
  "isSerialTrackable": true,
  "trackingType": "NOT_TRACKED",
  "things": [
    "F564X056",
    "F564X057"
  ],
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
```

### Изменить Товар 
Запрос на обновление существующего Товара.
Типы цен в ценах продаж и дополнительные поля обновляются как элементы вложенных коллекций:

+ Если в текущем объекте у какого-то из доп. полей / типов цен нет значения,
а в переданной коллекции оно есть - значение записывается в доп. поле / тип цены.
+ Если же у данного атрибута значение уже присутствует - оно перезаписывается на переданное.
+ Если у данного атрибута в составе объекта значение присутствует, однако оно отсутствует
в передаваемой в теле запроса коллекции (не передается совсем), то значение атрибута объекта не изменяется.

Для обновленя полей алкогольной продукции в теле запроса на обновление товара должен присутствовать объект **alcoholic**,
с вложенными в него полями, отражающими свойства алкогольной продукции:

+ **excise** - Содержит акцизную марку
+ **type**  - Код вида продукции
+ **strength** - Крепость
+ **volume** - Объем тары
Если в запросе на обновление товара, являющегося алкогольной продукцией, передать пустой объект **alcoholic**, с данного объекта
снимется отметка "Алкогольная продукция". Для того чтобы сделать товар, не являющийся алкогольной продукцией алкогольным, нужно в теле запроса
передать объект **alcoholic**, у которого хотя бы одно из свойств будет иметь значение.

При обновлении Товара с указанным массивом штрихкодов для каждого штрихкода требуется указать к какому типу относится штрихкод. 
Например, чтобы создать штрихкод с типом Code 128, в массив штрихкодов должен быть добавлен JSON-объект с полем code128 со значением штрихкода.

При включенном в основном интерфейсе серийном учете товаров, в запросе на обновление нельзя передать значение true полю **weighed**,
иначе возникнет ошибка, т.к. невозможен серийный учет весовых товаров.

> Пример запроса на обновление Товара
  
```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Тыква",
            "code": "pumpkin1",
            "externalCode": "456pumpkin",
            "description": "Тыква, Германия",
            "vat": 3,
            "effectiveVat": 3,
            "uom": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "supplier": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
                "type": "counterparty",
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
            "buyPrice": {
              "value": 54,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 3753,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "value": 3653,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              }
            ],
            "country": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/country/0238a888-c602-4e78-a199-d8f49c4d6c18",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/country/metadata",
                "type": "country",
                "mediaType": "application/json"
              }
            },
            "article": "Ar23",
            "weight": 100,
            "volume": 400,
            "packs": [
              {
                "id": "354ba98c-2cb9-11e6-8a84-bae5000000e3",
                "uom": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/2d1fdd55-d935-4d55-80d4-f6904b62ff46",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                    "type": "uom",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 40
              },
              {
                "uom": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/0dd4fe8b-e59e-486e-bde5-b52fe0e25415",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                    "type": "uom",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 101
              }
            ],
            "images": [
              {
                "filename":"birdimageNew.png",
                "content":"imageBase64"
              }
             ],
            "alcoholic": {
              "excise": true,
              "type": 3100,
              "strength": 0.6,
              "volume": 1.5
            },
            "barcodes": [
              {
                "code128": "code128barcode"
              }
            ]
          }'  
```  
  
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Товара.
  
```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "26b36824-2c83-11e6-8a84-bae50000001b",
  "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
  "updated": "2016-06-07 11:00:37",
  "name": "Тыква",
  "description": "Тыква, Германия",
  "code": "pumpkin1",
  "externalCode": "456pumpkin",
  "archived": false,
  "pathName": "",
  "vat": 3,
  "effectiveVat": 3,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
      "type": "image",
      "mediaType": "application/json",
      "size": 1,
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
      "value": 3753,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 3653,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
      "name": "Экспорт",
      "type": "boolean",
      "value": false
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
      "name": "Изготовитель",
      "type": "string",
      "value": "Колхоз \"Иваново\""
    }
  ],
  "country": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/country/0238a888-c602-4e78-a199-d8f49c4d6c18",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/country/metadata",
      "type": "country",
      "mediaType": "application/json"
    }
  },
  "buyPrice": {
    "value": 54,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "article": "Ar23",
  "weight": 100,
  "volume": 400,
  "packs": [
    {
      "id": "354ba98c-2cb9-11e6-8a84-bae5000000e3",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/2d1fdd55-d935-4d55-80d4-f6904b62ff46",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 40
    },
    {
      "id": "354ba98c-2cb9-11e6-8a84-bae5000004e3",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/0dd4fe8b-e59e-486e-bde5-b52fe0e25415",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 101
    }
  ],
  "barcodes": [
    {
      "code128": "code128barcode"
    }
  ],
  "alcoholic": {
    "excise": true,
    "type": 3100,
    "strength": 0.6,
    "volume": 1.5
  },
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

> Пример запроса на изменение Товара с дополнительными полями.
  
```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Тыква",
            "code": "pumpkin1",
            "externalCode": "456pumpkin",
            "description": "Тыква, Германия",
            "vat": 3,
            "effectiveVat": 3,
            "uom": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "supplier": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
                "type": "counterparty",
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
            "buyPrice": {
              "value": 54,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 3753,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "value": 3653,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              }
            ],
            "article": "Ar23",
            "weight": 100,
            "volume": 400,
            "attributes": [
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
                  "type": "attributemetadata",
                  "mediaType": "application/json"
                },
                "name": "Экспорт",
                "value": false
              },
              {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
                  "type": "attributemetadata",
                  "mediaType": "application/json"
                },
                "name": "Изготовитель",
                "value": "Колхоз \"Иваново\" "
              }
            ]
          }'  
```  
  
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновленного Товара.
  
  ```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "26b36824-2c83-11e6-8a84-bae50000001b",
  "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
  "updated": "2016-06-07 10:52:58",
  "name": "Тыква",
  "description": "Тыква, Германия",
  "code": "pumpkin1",
  "externalCode": "456pumpkin",
  "archived": false,
  "pathName": "",
  "vat": 3,
  "effectiveVat": 3,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
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
      "value": 3753,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 3653,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "attributes": [
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e54cd-2c80-11e6-8a84-bae50000009c",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e54cd-2c80-11e6-8a84-bae50000009c",
      "name": "Экспорт",
      "type": "boolean",
      "value": false
    },
    {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata/attributes/0c2e5dc5-2c80-11e6-8a84-bae50000009d",
        "type": "attributemetadata",
        "mediaType": "application/json"
      },
      "id": "0c2e5dc5-2c80-11e6-8a84-bae50000009d",
      "name": "Изготовитель",
      "type": "string",
      "value": "Колхоз \"Иваново\""
    }
  ],
  "buyPrice": {
    "value": 54,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "article": "Ar23",
  "weight": 100,
  "volume": 400,
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```

> Пример запроса на изменение Товара с упаковками.

```shell
  curl -X PUT
    "https://online.moysklad.ru/api/remap/1.3/entity/product/7944ef04-f831-11e5-7a69-971500188b19"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "Тыква",
            "code": "pumpkin1",
            "externalCode": "456pumpkin",
            "description": "Тыква, Германия",
            "vat": 3,
            "effectiveVat": 3,
            "uom": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                "type": "uom",
                "mediaType": "application/json"
              }
            },
            "supplier": {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
                "type": "counterparty",
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
            "buyPrice": {
              "value": 54,
              "currency": {
                "meta": {
                  "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                  "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                  "type": "currency",
                  "mediaType": "application/json"
                }
              }
            },
            "salePrices": [
              {
                "value": 3753,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f49fd",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              },
              {
                "value": 3653,
                "currency": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
                    "type": "currency",
                    "mediaType": "application/json"
                  }
                },
                "priceType": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
                    "type": "pricetype",
                    "mediaType": "application/json"
                  }
                }
              }
            ],
            "article": "Ar23",
            "weight": 100,
            "volume": 400,
            "packs" : [
              {
                "uom": {
                  "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
                    "type": "uom",
                    "mediaType": "application/json"
                  }
                },
                "quantity": 11,
                "barcodes": [
                  {
                    "code128": "code128barcode"
                  }
                ]
              }
            ]            
          }'  
```  
        
> Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновлённого Товара.
  
  ```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b",
    "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/product/metadata",
    "type": "product",
    "mediaType": "application/json"
  },
  "id": "26b36824-2c83-11e6-8a84-bae50000001b",
  "accountId": "6270cd18-2c7f-11e6-8a84-bae500000001",
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
  "updated": "2016-06-07 10:52:58",
  "name": "Тыква",
  "description": "Тыква, Германия",
  "code": "pumpkin1",
  "externalCode": "456pumpkin",
  "archived": false,
  "pathName": "",
  "vat": 3,
  "effectiveVat": 3,
  "discountProhibited": false,
  "uom": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
      "type": "uom",
      "mediaType": "application/json"
    }
  },
  "images": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/26b36824-2c83-11e6-8a84-bae50000001b/images",
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
      "value": 3753,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
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
    },
    {
      "value": 3653,
      "currency": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
          "type": "currency",
          "mediaType": "application/json"
        }
      },
      "priceType": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/context/companysettings/pricetype/672559f1-cbf3-11e1-9eb9-889ffa6f2222",
          "type": "pricetype",
          "mediaType": "application/json"
        },
        "id": "672559f1-cbf3-11e1-9eb9-889ffa6f2222",
        "name": "Цена для друзей",
        "externalCode": "cbcf493b-55bc-11d9-848a-00112f432222"
      }
    }
  ],
  "supplier": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/6313f1eb-2c7f-11e6-8a84-bae500000053",
      "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/counterparty/metadata",
      "type": "counterparty",
      "mediaType": "application/json"
    }
  },
  "buyPrice": {
    "value": 54,
    "currency": {
      "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.3/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/currency/metadata",
        "type": "currency",
        "mediaType": "application/json"
      }
    }
  },
  "packs" : [
    {
      "id": "6314188d-2c7f-11e6-8a84-bae500000055",
      "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.3/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.3/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
      },
      "quantity": 11,
      "barcodes": [
        {
          "code128": "code128barcode"
        }
      ]
    }
  ],
  "article": "Ar23",
  "weight": 100,
  "volume": 400,
  "isSerialTrackable": false,
  "trackingType": "NOT_TRACKED"
}
```  
