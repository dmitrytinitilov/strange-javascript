# \# Массивы

Допустим у нас есть массив чисел и мы хотим подсчитать их сумму. Для решения нам понадобится переменная sum, в которую мы будем накапливать нашу сумму. Изначально в ней будет 0

```js
var arr=[6,8,5,11];
console.log(arr[1]);//8

console.log(arr.length);//4
console.log(arr[arr.length-1]);//11 , всегда выводится содержимое последнего элемента

var sum = 0;

for (i=0;i<arr.length;i++) {
    sum = sum + arr[i]; //на каждом шаге цикла добавляем к sum i-й элемент массива
}
```

Попробуем работать с блоками через querySelectorAll. Создадим 10-ть блоков. Сделаем это через Emmet, то конструкция .block\*10 должна превратиться в

```html
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
    <div class="block"></div>
```

Поменяем с помощью JavaScript классы в наших блоках

```js
    var blockList = document.querySelectorAll('.block');

    for (i=0;i<blockList.length;i++) {
    blockList[i].className = 'changed';
    }
```

Попробуем создать набор картинок 1.jpg . Чтобы сделать это через Emmet наберите img\[src=1.jpg\]\*10 и нажмите tab. В результате получим

```html
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
    <img src="1.jpg" alt="">
```

Поменяем названия этих картинок на 2.jpg

```js
    var imgList = document.querySelectorAll('img');

    for (i=0;i<imgList.length;i++) {
        imgList[i].src = '2.jpg';
    }
```

**Практика:**

1. Есть массив чисел. Подсчитать количество чисел большее 10
2. Поменять класс в каждом втором блоке.
3. Поменять класс в каждом третьем блоке.
4. Вывести номера внутри каждого блока.
5. Есть массив с названиями картинок. Вывести галерею картинок
6. Есть два массива с названиями картинок\(жуки и бабочки\). Вывести картинки так, чтобы жуки и бабочки чередовались
7. Есть зеленые блоки с числами внутри. Те блоки, у которых число внутри больше 10, должны стать красными

8. Вывести картинки в стиле Masonry Grid \(пример сайт [http://pinterest.com](http://pinterest.com)\)



