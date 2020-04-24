# Создание и модификация узлов

**createElement и appendChild**

createElement - создает узел по названию тега

appendChild - переносит узел внутрь другого узла(см пример)

```js
var btn = document.createElement("BUTTON");        // Создаем элемент <button>
var t = document.createTextNode("CLICK ME");       // Создаем текстовый узел
btn.appendChild(t);                                // Добавляем текст в кнопку <button>
document.body.appendChild(btn);                    // Добавляем <button> в <body>
```

Обратите внимание, что если мы работаем с уже созданными элементами, то они просто переносятся, без создания копии!

[http://www.w3schools.com/jsref/met\_document\_createelement.asp](http://www.w3schools.com/jsref/met_document_createelement.asp)

**Наполнение элементов**

Созданный с помощью createElement элемент можно наполнять через стандартные свойства DOM-объекта.

```html
var banner = document.createElement('DIV');
banner.className = 'block';
banner.innerHTML = 'Летающий банер';
banner.style.position = 'fixed';
banner.style.top = '200px';
banner.style.left = '300px';
```

**insertBefore**

insertBefore, - добавляет элемент в  список дочерних элементов родителя перед указанным элементом.

```html
<div id="parentNode">
   <span id="childNode">foo bar</span>
</div>

<script>
//Создаем новый узел
var newNode = document.createElement("span");

//Добавляем перед childNode новый узел
parentNode.insertBefore(newNode,childNode);
</script>
```

**removeChild** - удаляет заданный узел из родительского узла 
[https://developer.mozilla.org/ru/docs/Web/API/Node/removeChild](https://developer.mozilla.org/ru/docs/Web/API/Node/removeChild)

Удаление элемента без указания его родителя

```js
var node = document.getElementById("nested");
if (node.parentNode) {
  node.parentNode.removeChild(node);
}
```

**cloneNode**  
[https://developer.mozilla.org/ru/docs/Web/API/Node/cloneNode](https://developer.mozilla.org/ru/docs/Web/API/Node/cloneNode)

```html
<div id="outer">
  <div id="inner">
  </div>
</div>

<div id="outer2">
</div>
```

Если мы сделаем appendChild без клонирования, то получим следующую ситуацию

```js
var inner = document.getElementById("inner");

var outer2 = document.getElementById("outer2");

outer2.appendChild(inner);
```

```html
<div id="outer">
</div>

<div id="outer2">
   <div id="inner">
   </div>
</div>
```

Воспользуемся клонированием

```js
var inner = document.getElementById("inner");
var clone = inner.cloneNode();

var outer2 = document.getElementById("outer2");

outer2.appendChild(clone);
```

```html
<div id="outer">
   <div id="inner">
   </div>
</div>

<div id="outer2">
   <div id="inner">
   </div>
</div>
```

**insertAdjacentHTML\(\)**
[https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML)


**Работа с атрибутами**

_setAttribute_ - устанавливает атрибут в элементе

https://developer.mozilla.org/ru/docs/Web/API/Element/setAttribute

Например, есть у нас кнопка

```html
<button>Hello World</button>
```

с помощью javascript'a сделаем ее неактивной

```js
var b = document.querySelector("button"); 

b.setAttribute("disabled", "disabled");
```

_getAttribute()_ - возвращает значение указанного атрибута элемента. Если элемент не содержит данный атрибут, могут быть возвращены null или "" (пустая строка);

https://developer.mozilla.org/ru/docs/Web/API/Element/getAttribute

```html
<input type="text" placeholder="здесь могла быть Ваша реклама">
```

```js
var b = document.querySelector("input"); 

var res = b.getAttribute("placeholder");

console.log('и '+res);//и здесь могла быть Ваша реклама
```

_hasAttribute_ - проверяет установлен ли атрибут. Возвращает true или false, в зависимости установлен наш атрибут в элементе или нет

```html
<input type="checkbox" checked>
```

```js
var b = document.querySelector("input"); 

b.hasAttribute("checked");
```
_removeAttribute_ - удаляет атрибут у элемента

```html
<input type="checkbox" checked>
```

```js
var b = document.querySelector("input"); 

b.removeAttribute("checked");
```

**Практика:**


3. Есть кнопка. При нажатии на нее появляется круг. При клике на любой из созданных кругов, он удаляется.

4. Даем возможность пользователю добавлять новые элементы в выпадающее меню \(ToDo List\).

5. Игра. В произвольном месте экрана появляются кружки - нужно успеть на них кликнуть, чтобы заработать баллы

6. Есть кнопка. При нажатии на кнопку в документ добавляются кружки.

7. Сделать так, чтобы в предыдущем задании кружки перекрашивались.

8. Добавить в предыдущее задание вторую кнопку и блок. При нажатии на кнопку все перекрашенные круги перемещаются в блок.

9. Сделать телефонный справочник. Есть список людей и их номеров телефонов. Есть форма, которая позволяет добавлять новых людей.

10. Рядом с каждой записью добавить кнопку удаления.

11. Добавить возможность редактирования каждой записи.



