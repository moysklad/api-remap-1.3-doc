# Список изменений

Список последних изменений включает в себя описание отличий между версиями API Remap 1.2 и 1.3.
Перечислены изменения и расширения возможностей существующих эндпоинтов, 
а также новые эндпоинты, которые позволяют эффективнее работать с API МоегоСклада. Более подробно с особенностями API 
МоегоСклада  можно ознакомиться в разделе [Workbook](https://dev.moysklad.ru/doc/api/remap/1.3/workbook/#workbook), 
а также по ссылкам на основные разделы данной документации.

Список изменений в версии 1.3 с момента её создания можно найти в [github репозитории](https://github.com/moysklad/api-remap-1.3-doc/blob/master/CHANGELOG.md)

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
