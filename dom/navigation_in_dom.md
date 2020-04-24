# Навигация по DOM

[https://learn.javascript.ru/traversing-dom](https://learn.javascript.ru/traversing-dom)

**.childNodes** - возвращает список всех узлов элемента

**.children** - возращает список всех нетекстовых узлов

**.parentNode** - родительский узел  
**parentElement**

**.firstChild** - первый узел-ребенок  
**.firstElementChild** - первый нетекстовый узел

**.lastChild** - последний узел-ребенок  
**.lastElementChild** - последний нетекстовый узел

**.previousSibling** - предыдущий соседний узел  
**.previousElementSibling** - предыдущий нетекстовый сосед

**.nextSibling**  **.nextElementSibling**

**Конвертация из HTMLCollection в Array**

var arr = Array.prototype.slice.call\( htmlCollection \)

var arr = \[\].slice.call\(htmlCollection\);

**Поиск элементов в DOM**

document.getElementsByTagName\(\)

document.getElementsByClassName\(\)

.querySelector - возвращает элемент, соответствующий указанному селектору

.querySelectorAll - возвращает список элементов, соответствующие указанному селектору

```js
elementList = document.querySelectorAll(selectors);
```

```html
<div class="block">
</div>
<div class="block">
</div>

<script>
    var first_block = document.querySelector("DIV"); //вернет ссылку на первый блок
</script>
```

**Практика:**  
1. Есть блоки с одним и тем же классом. Четные блоки окрасить в один цвет, нечетные блоки окрасить в другой \(использовать querySelectorAll\).  
2. Есть список блоков. Пронумеровать блоки в порядке возрастания \(использовать document.body.children\).  
3. Есть родительский блок и есть дети. Дети одного цвета, родитель другого. При клике на область родительского блока, родительский блок и дети меняются цветами.  
4.    Есть четыре блока. При нажатии на клавиши перемещаем «выделение» на активном блоке  
5.    В предыдущем задании делаем блок верхнего уровня  
6.    Иерархическое меню. Перемещаемся по нему с помощью клавиш, при нажатии enter меню выпадает

