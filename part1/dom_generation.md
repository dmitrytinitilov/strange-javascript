#Генерация DOM-объектов

**createElement и appendChild**
createElement - создает узел по названию тега
appendChild - переносит узел внутрь другого узла(см пример)

```js
var btn = document.createElement("BUTTON");        // Создаем элемент <button>
var t = document.createTextNode("CLICK ME");       // Создаем текстовый узел
btn.appendChild(t);                                // Добавляем текст в кнопку <button>
document.body.appendChild(btn);                    // Добавляем <button> в <body>
```

Обратите внимание, что если мы работаем с уже созданными элементами, то они просто переносятся, без создания копии!+

http://www.w3schools.com/jsref/met_document_createelement.asp

**Генерация картинки**

Еще один пример, затрагивающий генерацию элемента img

```js
var image = document.createElement("img");

image.src = 'odessa.jpg';

document.body.appendChild(image);
```

**Добавление блока внутрь существующего блока**

Допустим у нас уже есть какой-то блок на странице

```html
<div class="outer">
</div>
```
и мы хотим внутрь нашего блока добавить свежесозданный блок

```js
var outer = document.querySelector('.outer');

var inner = document.createElement("div");
inner.className = 'inner';

outer.appendChild(inner);
```

То есть последняя строчка показывает нам, что мы вполне можем добавить один DOM внутрь другого с помощью appendChild.

**Добавление нескольких элементов**

```js

for(i=0;i<10;i++) {
    var smallBlock = document.createElement("div");
    smallBlock.className = 'block';
    
    document.body.appendChild(smallBlock);
}
```

Обратите внимание, что мы в цикле каждый раз создаем объект через createElement. Дело в том, что appendChild не просто добавляет элемент в указанное место, а переносит также его со старого. То есть, если мы не будем создавать новый элемент, мы будем постоянно переносить блок со "старого" места на "старое"

**Полезное чтиво:**

1. Оптимизация генерации DOM-объектов  
https://howchoo.com/g/mmu0nguznjg/learn-the-slow-and-fast-way-to-append-elements-to-the-dom


**Практика:**

1. Сгенерировать 10 блоков и пронумеровать их
