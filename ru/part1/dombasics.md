# Добавляем DOM

**document.write**

Если мы хотим дописать html-код в body, можно воспользоваться методом document.write

```js
<script>
 document.write('<div id="block"></div>'); 
</script> 
 //добавляет данный код в документ
```

**document.getElementById\(\)**

document.getElementById - позволяет получить DOM-объект по его id

```html
<div id="block">
</div>

<script>
var obj = document.getElementById("block");
</script>
```

**Изменение встроенных css-свойств**

Допустим у нас есть синий блок, но с помощью Javascript мы сделаем его красным

Для этого будем использовать свойство style DOM-объекта

```html
<div id="block" style="width:100px;height:100px;background:black">
</div>

<script>
var obj = document.getElementById("block");
obj.style.backgroundColor='red';
</script>
```

**Считывание значений у input'a**

Допустим у нас есть input, и мы хотим считать оттуда значение.

```html
<input type="text" id="info">
```

```js
var obj = document.getElementById("info");
console.log(obj.value);// выведет значение содержимого
```

**innerHTML**

Свойство innerHTML DOM объекта обращается к внутреннему содержимому тега, которое находится между открывающим и закрывающим тегами.

```js
var obj = document.getElementById("block");
obj.innerHTML = 'Этот текст будет внутри блока'
```

Если у нас внутри блока находится текст, то вернется его содержимое. Например есть вот такой HTML

```html
<div class="outer">
    <div class="inner">
    </div>
</div>
```

```js

var block = document.querySelector('.outer');

var str = block.innerHTML

console.log(str);// <div class="inner"></div>

```

**Работа с классами**

Пример ниже выводит имя класса у блока с id "block1"

```html
<div class="bad_block" id="block1">
</div>

<script>
    var obj = document.getElementById("block1");
    console.log(obj.className);
</script>
```



**Практика:** 
    1. Есть два класса - первый окрашивает блок в синий цвет, другой в красный. Есть блок, окрашеный с помощью "синего" класса. Заменить его класс на "красный"
    2. Есть четыре блока с одним классом. При клике на блок добавляем к нему класс, который добавляет у него границу.
    3. Вывести картинку с помощью document.write  
    4. Вывести прямоугольник и поменять его цвет с помощью JavaScript  
    5. Вывести гистограмму  
    6. Вывести шахматную доску  
    7. Есть массив с названиями картинок, вывести галерею.  
    8. Генерируем блок произвольной ширины. Используем функцию Math.rand\(\);  
    9. Есть массив с цветами и массив с радиусами. Нужно вывести круги в произвольных местах экрана
    
