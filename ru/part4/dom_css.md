#Работа с CSS

**Получение значения свойства элемента**

https://developer.mozilla.org/en-US/docs/Web/API/Window/getComputedStyle

Для получения стилей элемента нам понадобится метод getComputedStyle объекта window. После чего мы получим объект со стилями элемента. Первым параметром этого метода должен быть DOM объект. Второй параметр предназначен для псевдоэлемента, если нам не нужен псевдоэлемент ставим null

```js
var elem1 = document.getElementById("elemId");
var style = window.getComputedStyle(elem1, null);
```

Если мы все-таки хотим получить свойства из псевдолемента, тогда вызов будет выглядеть вот так.

```js
var h3 = document.querySelector('h3'); 
result = getComputedStyle(h3, ':after').content;
```

После того как мы получили стили(CSSStyleDeclaration), можно вызвать от них метод getPropertyValue. 

```js
var elem = document.getElementById("elem-container");
var elemHeight = window.getComputedStyle(elem,null).getPropertyValue("height");
```

**classList**

http://frontender.info/the-classlist-api/
https://developer.mozilla.org/ru/docs/Web/API/Element/classList

Свойство classList позволяет более гибко модифицировать классы у элемента

.contains проверяет, есть ли класс в нашем объекте

```js
var obj = document.querySelector('.block');

obj.classList.contains('block') === true;

obj.classList.contains('bad_block') === false;
```

.toggle - добавляет класс, если его не было, убирает класс, если он был

**Добавление правил**

https://davidwalsh.name/add-rules-stylesheets

https://developer.mozilla.org/ru/docs/Web/API/CSSStyleSheet/insertRule

```js
sheet.insertRule("body {margin:0px}");
```

**CSS-переменные**

https://eager.io/blog/communicating-between-javascript-and-css-with-css-variables/