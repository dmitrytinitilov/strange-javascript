# #Модули и require

https://nodejs.org/docs/v0.4.4/api/modules.html

Подключим к нашему файлу модуль circle.js . Он находится в той же директории.

```js
var circle = require('./circle.js');
console.log( 'The area of a circle of radius 4 is '
           + circle.area(4));
```
Для создания модуля нам понадобится следующий код

```js
var PI = Math.PI;

exports.area = function (r) {
  return PI * r * r;
};

exports.circumference = function (r) {
  return 2 * PI * r;
};
```

Если мы хотим сделать доступной переменную или метод - добавляем ее в exports.

Все локальные переменные в модули будут private-переменными.

**О модулях**
https://www.youtube.com/watch?v=e1Ln1FrLvh8&list=PLYxzS__5yYQmHbpKMARP04F344zYRX91I&index=3

**Дополнительные материалы:**

https://darrenderidder.github.io/talks/ModulePatterns

**Практика:**

1. Написать модуль, который возвращает блок, заданного размера с фоновым изображением.