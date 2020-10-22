## GetFldImgList
*Контрол прикрепления набора изображений к документу с возможностью предпросмотра.*

Для ограничения загружаемых файлов можно указывать параметры:
* `FldVueFilesParams.Accept` - строка с перечислеными через запятую расширениями файлов. Например: .jpg, .pdf, image/*
* `FldVueFilesParams.MaxFileSize` - число указывающее максимальный размер файла в байтах 
* `FldVueFilesParams.Crop` - строка формата `<ширина(px)>x<высота(px)>` для обрезания фото под нужное соотношение сторон и размер. Например, `200x300`. Для поиска центра фото используется библиотека `SmartCrop`.
* `FldVueFilesParams.Width` - фото обрезается до указанной ширины в px.
* `FldVueFilesParams.CanAddUrls` - признак, что можно не только загружать фото, но вставлять ссылки на фото из интернета.
 
```go
    t.GetFldImgList("images", "фото", [][]int{{4, 1}}, t.FldVueImgParams{Crop: "200x300", CanAddUrls: true}, "col-8")
``` 

<img src="flds/fld_img_list_01.jpg" style="max-width: 600px; width: 90%">

Загруженные файлы хранятся в папке `images/<тип документа>/<id документа>`

<img src="flds/fld_img_list_02.jpg" style="max-width: 300px; width: 90%">