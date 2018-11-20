#Работа с селекторами

Изначально основной задачей JavaScript'a было модификация страницы и реакция на действия пользователя.

**document.querySelector**

Допустим у нас есть div с классом .block

```html
<div class="block">
</div>
```

Мы хотим начать работать с ним через JavaScript. В этом нам поможет стандартная функция document.querySelector, которая по селектору возвращает DOM-объект.

```js
var rect = document.querySelector('.block');
```

Важный момент состоит в том, что в querySelector мы можем применять любой CSS-селектор!

**.innerHTML**

Получения ссылки на DOM-объект для нас безусловно мало, хочется с ним, что-то сделать(для чего ж мы эту ссылку получали!?). Для начала давайте добавим текст внутрь

```js
rect.innerHTML = 'теперь в прямоугольнике есть текст';
```

**.className**

Давайте поменяем класс у блока, сделать это можно вот так

```js
rect.className = 'unblock';
```

Обратите внимание, что тут никаких точек не нужно, потому что это имя класса, а не селектора.

**document.querySelectorAll**

Но что делать, если у нас несколько элементов с одним классом. В этом случае document.querySelector вернет лишь первый из них.

Для решения этой проблемы есть функция document.querySelectorAll

Допустим у нас есть три div'а с классом block

```html
<div class="block">
</div>
<div class="block">
</div>
<div class="block">
</div>
```

С помощью querySelectorAll можно получить коллекцию блоков

```js
var blocksCollection = document.querySelectorAll('.block');
```

Если мы хотим работать с первым блоком, то нужно будет обратиться к нулевому элементу коллекции blocksCollection[0]

Общее количество элементов коллекции можно получить через свойство .length

```js
var blocksCollection = document.querySelectorAll('.block');

blocksCollection[0].innerHTML = 'Первый элемент коллекции';
blocksCollection[1].innerHTML = 'Второй элемент коллекции';
blocksCollection[2].innerHTML = 'Третий элемент коллекции';

console.log('Количество элементов '+blocksCollection.length);
```

**Написание собственной библиотеки**

Допустим мы хотим, чтобы div с атрибутом stripes=ok становился полосатым. При этом, если пользователь захочет использовать нашу библиотеку такие div'ы ему придется подготавливать самому (о чем мы его предупредим в описании библиотеки... наверное). То есть пользователь подготавливает файл следующего вида

```html
<div class="block" stripes=ok>
</div>
```

Теперь наша задача подготовить два файла stripes.js и stripes.css

stripes.css будет содержать css-класс, который и будет добавлять полосы

```css
.stripes {
    background-image:repeating-linear-gradient(-45deg,
        transparent,
        transparent 20px,
        black 20px,
        black 40px
    )
}
```

и stripe.js, который будет добавлять этот класс к div'ам с атрибутом stripes=ok

```js
var block = document.querySelector('[stripes=ok]');

//добавим наш класс к текущим
block.className += ' stripes';
```

Теперь, чтобы наша библиотека заработала у пользователя, нужно, чтобы он подключил нашы css и js-файлы к своему коду.

То есть у пользователя должен получится вот такой вот код

```html
<link rel="stylesheet" href="stripes.css">

<div class="block" stripes=ok>
</div>

<script src="stripes.js">
</script>
```

**Практика:**

1. Поменять цвет блока с помощью JavaScript
2. Есть десять блоков. Поменять блок с заданным номером.Номер задается через переменную i, либо вводится с клавиатуры через prompt
3. Есть список. С помощью js сделать так, чтобы подпункты скрылись.