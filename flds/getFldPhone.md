[Flds](/flds/README.md)

## GetFldPhone
*поле 'номер телефона'*

* маска для ввода номера
* иконка телефона

```go
    t.GetFldPhone("phone", "телефон", [][]int{{3,1}})
```
<img src="flds/fld_phone_01.jpg" style="max-width: 400px; width: 90%">

в базе данных хранится как строка
при сохранении в базу стираются все другие символы кроме цифр
если номер начинается на 8, то автоматически заменяется на 7

<img src="flds/fld_phone_02.jpg" style="max-width: 400px; width: 90%">
