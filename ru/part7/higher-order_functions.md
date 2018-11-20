# Техника map-reduce

**map**

```js
var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) {
  return num * 2;
});
```

**reduce**

```js
[0, 1, 2, 3, 4].reduce(function(previousValue, currentValue, currentIndex, array) {
  return previousValue + currentValue;
});
```

**Преобразование HTMLCollection в Array**

```js
var arr = [].slice.call(htmlCollection);
```

**filter**

```js
var words = ["spray", "limit", "elite", "exuberant", "destruction", "present"];

var longWords = words.filter(function(word){
  return word.length > 6;
});
```

**Полезное чтиво:**

1. Map, Reduce, Filter https://danmartensen.svbtle.com/javascripts-map-reduce-and-filter

**Практика:**
1.	Посчитать сумму чисел
2.	Посчитать сумму квадратов чисел
3.	Есть блоки. Сделать кнопки для одновременного изменения цвета, поворота, скругления, восстановления обратно
4.	Есть массив чисел. С помощью функции filter получить массив простых чисел
