# Список изменений

В разделе перечислены изменения и расширения возможностей существующих эндпоинтов, а также новые эндпоинты,
 которые позволяют эффективнее работать с API МоегоСклада.

Более подробно с особенностями API МоегоСклада  можно ознакомиться в
 разделе [Workbook](https://dev.moysklad.ru/doc/api/remap/1.3/workbook/#workbook), а также по ссылкам на основные разделы данной документации.

Список изменений в версии 1.3 с момента её создания можно найти в [github репозитории](https://github.com/moysklad/api-remap-1.3-doc/blob/master/CHANGELOG.md)

## Нотификация в изменениях API
Чтобы узнавать об изменениях в документации и api, вы можете подписаться на нотификации об изменении документации в github.
Для этого:

- установите любой RSS reader (например, [RSS Feed Reader](https://chrome.google.com/webstore/detail/rss-feed-reader/pnjaodmkngahhkoihejjehlcdlnohgmp) для chromium или [FeedBro](https://addons.mozilla.org/en-US/firefox/addon/feedbroreader) для Firefox)
- добавьте https://github.com/moysklad/api-remap-1.3-doc/commits/master.atom
- при любом изменении документации придёт нотификация и можно посмотреть, что именно изменилось.

## Отличия API Remap 1.3 от API Remap 1.2
### Добавлено
- В [изображениях](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-izobrazhenie) и
 [файлах](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-fajly) появился объект `download`.

### Изменено
- Изменения в работе с [изображениями](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-izobrazhenie)
  - Поле downloadHref перемещено из meta в download
  - Изменилась miniature и tiny
    - поле href переименовано в downloadHref
    - значение поле type изменено с `image` на `file`
- Изображение [сотрудника](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-sotrudnik) теперь не image, а avatar.
- Автором [Задач](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-zadacha), комментариев к задачам и [Событий Контрагента](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-kontragent-sobytiq-kontragenta) может быть не только Сотрудник, но и Приложение
- Поле `vat` в позициях [Документов](https://dev.moysklad.ru/doc/api/remap/1.3/documents/) сделано nullable для возможности различать null и 0.

### Удалено
- В сущностях [Группа товаров](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-gruppa-towarow), [Товары](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-towar), [Комплекты](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/№suschnosti-komplekt), [Услуги](https://dev.moysklad.ru/doc/api/remap/1.3/dictionaries/#suschnosti-usluga), позиции [Документов](https://dev.moysklad.ru/doc/api/remap/1.3/documents/) удалено поле `vatEnabled`, которое являлось способом обойти обязательность поля `vat`
- Поле **product** у материалов и продуктов [Тех. карт](https://dev.moysklad.ru/doc/api/remap/1.3/documents/#dokumenty-teh-karta)
