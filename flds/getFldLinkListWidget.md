[Flds](/flds/README.md)

## GetFldLinkListWidget
*виджет для редактирования связей многие-к-многим*

Если есть таблица связи многие-к-многим, то в каждую из записей можно вставить виджет, позволяющий отражать/редактировать связи. Таблица связи должна иметь название вида `<название первой таблицы>_<название второй таблицы>_link`.

Например, есть таблицы:
- `department` (Отделы)
- `region` (Регионы)
- `department_region_link` (связь департаментов и регионов)

ВАЖНО: в таблице-связи нужно в раздел Sql добавить параметр IsUniqLink: true

<img src="flds/list_widget_sql_isuniq.jpg" style="max-width: 250px; width: 90%">

Тогда в описании полей в файлах `docs/region/main.go` и `doc/department/main.go` можно использовать такую конструкцию:

```go
    t.GetFldLinkListWidget("region_department_link", [][]int{{2,1}}, "col-4", nil)
```

Тогда на экране редактирования `Региона` будет так:

<img src="flds/list_widget_region.png" style="max-width: 500px; width: 90%">

Списком будут отображаться отделы, связанные с данным регионам. С возможностью добавления новых и удаления существующих.

На экране редактирования `Отдела` будет так:

<img src="flds/list_widget_department.png" style="max-width: 500px; width: 90%">

Списком будут отображаться регионы, связанные с данным регионам. С возможностью добавления новых и удаления существующих.

```
пример с дополнительными полями
t.GetFldLinkListWidget("user_department_link", [][]int{{2, 1}}, "col-8", map[string]interface{}{
				"tableDependRoute": "employee",
				"readonly": "!isAdmin",
				"flds": "[[" +
					"{name: 'position', label: 'должность', type: 'string', columnClass: 'col-6'}, " +
					"{name: 'is_boss', label: 'начальник', type: 'checkbox', columnClass: 'col-6'}" +
					"]]",
				"slotOtherFlds": "<q-item-label caption><q-badge v-if='slotProps.item.is_boss' label='начальник' class='q-mr-sm'/>  <span>{{slotProps.item.position}}</span></q-item-label>",
			})
```

