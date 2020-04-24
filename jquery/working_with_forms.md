# #COFFEE Работа с формами

Обращение к input'ам разного типа можно делать через селекторы с двоиточеем. Например

```html
<input type="text">
```

Получим значения с этого input'a
```js
$(':text').val()
```


:button

:checkbox

:checked

:disabled

:enabled

:focus

:file

:image

:input

:password

:radio

:reset

:selected

:submit

:text

**События форм**

.blur()

.change()

.focus()

.select()

.submit()



Чтобы получить значение элемента, нужно сделать
```js
$("select.foo").val();
```

**Практика:**

1. Есть массив "использованных" логинов. При вводе логина делаем проверку свободен ли он.

2. Реализовать такую же реакции на получение фокуса, как на http://webfont.ru/