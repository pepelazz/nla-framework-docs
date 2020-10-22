[Flds](/flds/README.md)

## GetFldFiles
*Контрол для прикрепления файлов к документу*

Для ограничения загружаемых файлов можно указывать параметры:
* `FldVueFilesParams.Accept` - строка с перечислеными через запятую расширениями файлов. Например: _.jpg, .pdf, image/*_
* `FldVueFilesParams.MaxFileSize` - число указывающее максимальный размер файла в байтах 

```go
    t.GetFldFiles("files", "файлы", [][]int{{3, 1}}, t.FldVueFilesParams{Accept: "jpg,png", MaxFileSize: 100000})
```
<img src="flds/fld_files_01.jpg" style="max-width: 400px; width: 90%">

Загруженные файлы хранятся в папке `uploaded_files/<тип документа>/<id документа>`

<img src="flds/fld_files_02.jpg" style="max-width: 300px; width: 90%">
