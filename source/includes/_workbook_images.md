## Работа с Изображениями в Товарах, Модификациях и Комплектах

Иногда требуется добавить или изменить несколько изображений для товара. Это можно сделать несколькими способами: 
обновить список изображений в рамках обновления товара или воспользоваться эндпоинтами для работы с изображениями.
 
 Для добавления изображения нужно задать поля `filename` и `context`, соответствующие названию и содержанию файла,
  закодированному в Base64, соответственно.
 Если нужно добавить или дублировать уже существующее изображение, то можно указать его `meta`.
 
 Например, нужно создать Товар с несколькими изображениями. Это можно сделать следующим образом:
 
 > Запрос на создание товара с двумя изображениями
 
  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '{
            "name": "simplegood",
            "images": [
              {
                "filename": "birdimage.png",
                "content": "Base64"
              },
              {
                "filename": "birdimage2.png",
                "content": "Base64"
              }                
            ]
          }'  
  ```
 
 > Response 200 (application/json)
 Успешный запрос. Результат - JSON представление созданного Товара с изображениями.
   
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
   "name": "simplegood",
   "code": "00006",
   "externalCode": "0bmPIvHxgEDlNIZrZ6GLt2",
   "archived": false,
   "pathName": "",
   "images": {
     "meta": {
       "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images",
       "type": "image",
       "mediaType": "application/json",
       "size": 2,
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

Стоит заметить, что в ответе нет перечисления всех изображений, а лишь указана `meta` для коллекции. Чтобы получить 
список изображений в рамках товара необходимо дабавить в конец запроса `&expand=images&limit=100` при 
создании, получении или обновлении товара.

> Запрос на получение Товара с указанным id.

```shell
curl -X GET
  "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004&expand=images&limit=100"
  -H "Authorization: Basic <Credentials>"
```

> Response 200 (application/json)
 Успешный запрос. Результат - JSON представление запрошенного Товара с изображениями.
   
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
   "name": "simplegood",
   "code": "00006",
   "externalCode": "0bmPIvHxgEDlNIZrZ6GLt2",
   "archived": false,
   "pathName": "",
   "images": {
     "meta": {
       "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images",
       "type": "image",
       "mediaType": "application/json",
       "size": 2,
       "limit": 1000,
       "offset": 0
     },
     "rows": [
       {
         "meta": {
           "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images/f2728180-6afd-4d37-8a13-f3b48069bbb6",
           "type": "image",
           "mediaType": "application/json"           
         },
         "title": "birdimage",
         "filename": "birdimage.png",
         "size": 14052,
         "updated": "2019-01-24 16:55:24.567",
         "download": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6",
           "type": "file",
           "mediaType": "application/octet-stream"       
         },
         "miniature": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6?miniature=true",
           "type": "file",
           "mediaType": "image/png"
         },
         "tiny": {
           "downloadHref": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/ebb10350-0272-45db-9d33-ca5a01fd5543/t.png",
           "type": "file",
           "mediaType": "image/png"
         }
       },
       {
         "meta": {
           "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
           "type": "image",
           "mediaType": "application/json"
         },
         "title": "birdimage1",
         "filename": "birdimage1.png",
         "size": 14052,
         "updated": "2019-01-24 16:55:25.047",
         "download": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
           "type": "file",
           "mediaType": "application/octet-stream"       
         },
         "miniature": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f?miniature=true",
           "type": "file",
           "mediaType": "image/png"
         },
         "tiny": {
           "downloadHref": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/c960c879-8128-4511-addf-b933f37dc0d4/t.png",
           "type": "file",
           "mediaType": "image/png"
         }
       }
     ]
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

Теперь рассмотрим другой вариант работы с изображениями. Предположим, что есть товар, и нужно обновить его изображения. 
Для этого можно воспользоваться эндпоинтом для работы с изображениями товаров.

> Запрос на обновление изображений у товара

  ```shell
  curl -X POST
    "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images"
    -H "Authorization: Basic <Credentials>"
    -H "Content-Type: application/json"
      -d '[
            {
              "filename": "birdimage.png",
              "content": "Base64"
            },
            {
              "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
                "type": "image",
                "mediaType": "application/json"
              }        
            }                
          ]'  
  ```

> Ответ - обновленный список изображений товара

```json

     [
       {
         "meta": {
           "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images/f2728180-6afd-4d37-8a13-f3b48069bbb6",
           "type": "image",
           "mediaType": "application/json"
         },
         "title": "birdimage",
         "filename": "birdimage.png",
         "size": 14052,
         "updated": "2019-01-24 16:55:24.567",
         "download": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6",
           "type": "file",
           "mediaType": "application/octet-stream"       
         },
         "miniature": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/f2728180-6afd-4d37-8a13-f3b48069bbb6?miniature=true",
           "type": "file",
           "mediaType": "image/png"
         },
         "tiny": {
           "downloadHref": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/ebb10350-0272-45db-9d33-ca5a01fd5543/t.png",
           "type": "file",
           "mediaType": "image/png"
         }
       },
       {
         "meta": {
           "href": "https://online.moysklad.ru/api/remap/1.3/entity/product/bd1c0a3e-95ee-11e6-8a84-bae500000004/images/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
           "type": "image",
           "mediaType": "application/json"
         },
         "title": "birdimage1",
         "filename": "birdimage1.png",
         "size": 14052,
         "updated": "2019-01-24 16:55:25.047",
         "download": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f",
           "type": "file",
           "mediaType": "application/octet-stream"       
         },
         "miniature": {
           "downloadHref": "https://online.moysklad.ru/api/remap/1.3/download/933e41ac-1946-4bf0-9b21-51f2051f3e9f?miniature=true",
           "type": "file",
           "mediaType": "image/png"
         },
         "tiny": {
           "downloadHref": "https://online.moysklad.ru/static/tinyimage/f2aab4d2-1fd3-11e9-ac12-000800000001/tinyimage/c960c879-8128-4511-addf-b933f37dc0d4/t.png",
           "type": "file",
           "mediaType": "image/png"
         }
       }
     ]
```

Подробнее про работу с изображениями можно прочитать 
[тут](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-izobrazhenie).
