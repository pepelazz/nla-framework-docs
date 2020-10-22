[Flds](/flds/README.md)

## GetFldJsonList
*Редактируемый список, которые хранится в базе данных как json массив.*

Необходимо указать типы полей в массиве и ширину (класс “col-..”.). `[][]int{{1,1}}` не на что не влияет в данном случае, так как тут не сетка, а строка, в которой поля выводятся по порядку. 

Суммарно ширины всех колонок не должны превышать 12. Иначе правая кнопка с иконкой удаления окажется за границей списка.

Для элементов списка можно указать иконку. Можно не указывать.

При удалении элемент списка физически не удаляется, а отмечается как удаленный. Посмотреть список удаленных элементов можно нажав иконку справа вверху.  

В списке удаленных элементов доступна функция по восстановлению элемента.

Пример:

```go
    t.GetFldJsonList("phone", "телефоны", [][]int{{3,1}}, t.FldVueJsonList{
      Icon: "https://image.flaticon.com/icons/svg/2933/2933290.svg",
      Flds: []t.FldType{
         t.GetFldString("number", "номер", 50, [][]int{{1,1}}, "col-5").SetIsBorderless(),
         t.GetFldString("name", "имя", 50, [][]int{{1,2}}, "col-7").SetIsBorderless(),
      },
    }, "col-8"),
```

<img src="flds/json_list_01.png" style="max-width: 700px; width: 90%">

```go
    t.GetFldJsonList("email", "email", [][]int{{2,1}}, t.FldVueJsonList{
      Icon: "https://image.flaticon.com/icons/svg/893/893292.svg",
      Flds: []t.FldType{
         t.GetFldString("email", "email", 50, [][]int{{1,1}}, "col-5").SetIsBorderless(),
         t.GetFldString("name", "имя", 50, [][]int{{1,2}}, "col-5").SetIsBorderless(),
         t.GetFldCheckbox("is_work", "рабочий", [][]int{{1,3}}, "col-2"),
      },
    }, "col-8"),
```
<img src="flds/json_list_02.png" style="max-width: 700px; width: 90%">
