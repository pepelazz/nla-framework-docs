## Функции создания полей

|  функция      | описание    |  тип в Postgres   |
| :------------- | :---------- | -----------: |
| [GetFldTitle](/flds/getFldTitle.md)  | название документа   | char    |
| [GetFldRef](/flds/getFldRef.md)   | поле-ссылка на другой документ | int  |
| [GetFldCheckbox](/flds/getFldCheckbox.md) | контрол checkbox | bool |
| [GetFldLinkListWidget](/flds/getFldLinkListWidget.md)   | виджет для редактирования связей многие-ко-многим | -  |
| [GetFldVueCompositionRefList](/flds/getFldVueCompositionRefList.md)   | виджет для редактирования связей один-ко-многим | -  |
| [GetFldJsonList](/flds/getFldJsonList.md)   | редактируемый список, которые хранится в базе данных как json массив | jsonb  |
| [GetFldFiles](/flds/getFldFiles.md) | контрол для прикрепления файлов к документу | jsonb |
| [GetFldImgList](/flds/getFldImgList.md) | контрол прикрепления набора изображений к документу с возможностью предпросмотра | jsonb |
| [GetFldImg](/flds/getFldImg.md) | контрол прикрепления одного изображения к документу с возможностью предпросмотра | jsonb |
| [GetFldPhone](/flds/getFldPhone.md) | номер телефона | string |
| [GetFldEmail](/flds/getFldEmail.md) | email | string |
| [GetFldSelectString](/flds/getFldSelectString.md) | выбор из списка | string |
| [GetFldSelectMultilple](/flds/getFldSelectMultilple.md) | выбор нескольких значений из списка | []text |
