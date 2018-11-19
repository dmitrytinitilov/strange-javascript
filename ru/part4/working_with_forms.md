# Работа с формами

**Получение значения из input'a**

Допустим у нас есть поле для ввода текста

```html
<input type="text" id="name"> 
```

Чтобы получить значение того, что введено в input'e используем свойство .value

```js
var obj = document.getElementById("name");

console.log(obj.value);
```

**Отправка формы**

Допустим у нас есть следующая форма

```html
<form action="#" method="GET">
    <input type="text" name="login">
    <input type="password" name="password">
    <input type="submit">
</form>
```

Мы можем отправить ее несколькими способами:

1. Отправка формы

```js
var form = document.querySelector('form');

form.submit();
```

2. Генерация клика на форме отправки

```js

var submitBtn = document.querySelector('input[type=submit]');

submitBtn.click();
```

**События**

.focus - при получении фокуса 

```js
var obj = document.getElementById("name");

obj.onfocus = function() {
    alert('Фокус здесь');
}
```

.blur - при потере фокуса


**onchange** 

при изменении значения в SELECT'e и input type="file"

.checked

 document.getElementById("myCheck").checked = true;
 
**oninput**

```js
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100
+<input type="number" id="b" value="50">
=<output name="x" for="a b"></output>
</form>
```

```js
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" name="b" value="50" /> +
    <input type="number" name="a" value="10" /> =
    <output name="result"></output>
</form>
```
 

**Дополнительные ссылки:**
Выразительный JavaScript про формы
https://habrahabr.ru/post/245731/

Проблемы со всплытием focus, blur, change
http://www.quirksmode.org/blog/archives/2008/04/delegating_the.html


**Практика:**

1. Вводим данные в input. Набранный текст выводится рядом с input'ом

2. При вводе логина делаем автопроверку свободен ли он. Если логин свободен обводим input зеленой рамочкой.

3. Сделать всплывающие подсказки при вводе текста.

4. Сделать конвертор валют

5. Чекбоксы. Сделать кнопку, которая убирает выделение со всех чекбоксов

6. Сделать калькулятор