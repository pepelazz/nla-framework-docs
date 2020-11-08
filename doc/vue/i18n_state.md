[Настройка документа](/doc/README.md) / [vue](/doc/vue/README.md)

## Локализация состояний и списков переменных

#### В случае когда варианты перечислены в поле типа select

Например, есть поле в котором есть три состояния:

* draft: черновик
* opened: открыто
* closed: закрыто

Записываем через `GetFldSelectString`
```go
    t.GetFldSelectString("state", "статус", 50, [][]int{{3,2}}, []t.FldVueOptionsItem{{"черновик", "draft"}, {"открыто", "opened"}, {"закрыто", "closed"}})
``` 

в файле utils.js создается функция

```js
const i18n_football_match_state = (v) => {
	const d = {
		draft: 'черновик',
		opened: 'открыто',
		closed: 'закрыто'
	}
	return Array.isArray(v) ? v.map(v1 => d[v1]) : d[v]
}
```

к которой можно обращаться в коде шаблонов через `this.$utils.i18n_football_match_state`

например:
`<q-item-label caption>{{$utils.i18n_football_match_state(item.state)}}</q-item-label>`  
 
***
#### В случае когда нужно передать ключ-значение без использования GetFldSelectString

В файле с описанием документа создаем переменную типа `map[string]string` и заполняем ее нужными значениями:
```go 
 var stateI18n = map[string]string{
  	"draft":      "новое задание",
  	"rejected":   "отклонена",
  	"in_casting": "передана в литейный цех",
  	"finished":   "выполнен",
  }
```

далее в разделе описания параметров Vue прописываем строку для GloablI18n:
```
Vue: t.DocVue{
 			RouteName:      name,
 			MenuIcon:       menu_icon,
 			BreadcrumbIcon: breadcrumb_icon,
 			Roles:          []string{},
 			GloablI18n:     map[string]map[string]string{fmt.Sprintf("i18n_%s_state", name): stateI18n},
},
```

результат будет такой же - в utils.js будет создана функция локализации, к которой в шаблонах можно будет обращаться через `this.$utils.i18n_football_match_state`