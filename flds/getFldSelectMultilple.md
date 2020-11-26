[Flds](/flds/README.md)

## GetFldSelectMultilple
*выбор нескольких значений из списка*

Выбор из выпадающего списка. В массив `[]t.FldVueOptionsItem` передаем список вариантов, в которых Label это надпись, которая будет на экране, а Value это значение, которое будет хранится в базе. Важно чтобы Value было без пробелов, иначе будет ошибка в javascript.

```go 
    t.GetFldSelectMultilple("cargo_damage_reason", "причины повреждения груза", [][]int{{16,1}}, []t.FldVueOptionsItem{{"состояние груза перед отправкой", "condition_of_cargo_before_shipment"}, {"нарушение температурного режима", "violation_of_the_temperature_regime"}, {"нарушение условий транспортировки", "violation_of_transportation_conditions"}})
```

<img src="flds/fld_select_multiple_01.jpg" style="max-width: 400px; width: 90%">