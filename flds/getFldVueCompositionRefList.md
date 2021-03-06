[Flds](/flds/README.md)

## GetFldVueCompositionRefList
*виджет для редактирования связей один-к-многим*

Если есть между таблицами есть связь один-ко-многим, то на экране можно вставить виджет, позволяющий отражать/редактировать связанные записи.

Например, есть таблицы:
- `building_object` (Строительные объекты)
- `building_object_event` (События)

Между `building_object` и `building_object_event` есть связь один-ко-многим: в таблице `building_object_event` есть поле `building_object_id` связывающее `событие` с конктретным `строительным объектом`.

Тогда в описании полей в файле `docs/buildingObject/main.go`  можно использовать такую конструкцию:

```go
    doc.Init()
    // !!! ВАЖНО: поле необходимо добавлять после инициализации документа
    doc.AddFld(t.GetFldVueCompositionRefList(&doc, t.VueCompRefListWidgetParams{
    		Label: "события", // название списка, которе выводится на экране 
    		FldName: "event_list", // название поля. Любое, в формате snake_case. На основе этого названия формируется название компоненты во vue.
    		TableName: "building_object_event", // название связанной таблицы, из которой будут выгружаться записи
    		RefFldName: "building_object_id", // название поля в связанной таблицы, по которому осуществляется связь
    		Avatar: "https://www.flaticon.com/svg/static/icons/svg/3174/3174440.svg", // иконка, которая выводится в списке
    		NewFlds: []t.FldType{
    			t.GetFldString("title", "название", 300, [][]int{{1,1}}).SetIsRequired(),
    			t.GetFldDate("event_date", "дата события", [][]int{{2,2}}),
    			t.GetFldString("comment", "описание события", 1000, [][]int{{3,1}}),
    			t.GetFldTag("event_tags", "тэги события", [][]int{{3,2}}),
    		}, // список полей, которые заполняются при добавлении новой записи
    		TitleTemplate: `
    			<q-item-label>{{v.title}}</q-item-label>
    			<q-item-label caption>{{$utils.formatPgDate(v.event_date)}}</q-item-label>
    		`, // шаблон для названия в списке (vue синтаксис)
    	}, [][]int{{5,1}}, "col-4"))
```

Тогда на экране редактирования `Строительного объекта` будет так:

<img src="flds/fld_ref_list_01.jpg" style="max-width: 400px; width: 90%">

Списком будут отображаться события, связанные со строительным объектом. С возможностью добавления новых и удаления существующих.

#### Список параметров виджета
|  параметр      | описание      | обязательный |
| :------------- | :----------  | ----------:  |
| Label | название списка, которе выводится на экране   | да|
| FldName | название поля. Любое, в формате snake_case. На основе этого названия формируется название компоненты во vue.   | да|
| TableName | название связанной таблицы, из которой будут выгружаться записи   | да|
| RefFldName | название поля в связанной таблицы, по которому осуществляется связь   | да|
| Avatar | иконка, которая выводится в списке   | да|
| NewFlds | список полей, которые заполняются при добавлении новой записи   | |
| TitleTemplate | шаблон для названия в списке (vue синтаксис)   | |
| IsHideDelete | убрать возможность удаления   | |
| IsHideAdd | убрать возможность добавления  | |


