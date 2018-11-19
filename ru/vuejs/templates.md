#Шаблоны

**Базовые шаблоны**

Значение из data.msg подставится в такой шаблон

```html
<span>Message: {{ msg }}</span>
```

v-html  позволяет устанавливать innerHTML div'а
```html
<div v-html="innerHTML of that div"></div>
```

**Привязка аргументов**

```html
<a v-bind:href="url"></a>
```

**Привязка событий**

```html
<a v-on:click="doSomething">
```

Запуск event.preventDefault() на событии
<form v-on:submit.prevent="onSubmit"></form>

**Фильтры**

Мы можем применить к сообщению фильтры

```html
{{ message | capitalize }}
```

```js
new Vue({
  // ...
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
```

Можно добавить несколько фильтров

```
{{ message | filterA | filterB }}
```

**Сокращенные записи**

Для v-bind

```html
<!-- full syntax -->
<a v-bind:href="url"></a>
<!-- shorthand -->
<a :href="url"></a>
```

Для v-on

```html
<!-- full syntax -->
<a v-on:click="doSomething"></a>
<!-- shorthand -->
<a @click="doSomething"></a>
```

**Полезное чтиво:**

1. 7 способов определить шаблон во VueJS  
https://medium.com/js-dojo/7-ways-to-define-a-component-template-in-vuejs-c04e0c72900d
