# Прототипы

https://learn.javascript.ru/prototype

```js
var animal = {
  eats: true
};
var rabbit = {
  jumps: true
};

rabbit.__proto__ = animal;

// в rabbit можно найти оба свойства
alert( rabbit.jumps ); // true
alert( rabbit.eats ); // true
```


**hasOwnProperty**

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty

Метод hasOwnProperty позволяет проверять является ли данное свойство собственным свойством объекта или же оно взято из прототипа.

```js

rabbit.hasOwnProperty('jumps');//true

rabbit.hasOwnProperty('eats');//false

```

**prototype**

```js
var animal = {
  eats: true
};

function Rabbit(name) {
  this.name = name;
}

Rabbit.prototype = animal;

var rabbit = new Rabbit("Кроль"); //  rabbit.__proto__ == animal

alert( rabbit.eats ); // true
```

**constructor**

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor

свойство прототипа constructor указывает на конструктор объекта, то есть
```js
  rabbit.__proto__.constructor === Rabbit
```

Иногда в коде Вы можете столкнуться со следующей строчкой.

```js
Car.prototype.constructor = Car;
``` 

Что делает эта строчка? И зачем?

http://stackoverflow.com/questions/9343193/why-set-prototypes-constructor-to-its-constructor-function

http://stackoverflow.com/questions/8453887/why-is-it-necessary-to-set-the-prototype-constructor

**Object.create**

Object.create -создает новый объект, используя в качестве прототипа, объект указанный в параметрах. 

```js
// Shape — суперкласс
function Shape() {
  this.x = 0;
  this.y = 0;
}

// метод суперкласса
Shape.prototype.move = function(x, y) {
  this.x += x;
  this.y += y;
  console.info('Фигура переместилась.');
};

// Rectangle — подкласс
function Rectangle() {
  Shape.call(this); // вызываем конструктор суперкласса
}

// подкласс расширяет суперкласс
Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle;

var rect = new Rectangle();

console.log('Является ли rect экземпляром Rectangle? ' + (rect instanceof Rectangle)); // true
console.log('Является ли rect экземпляром Shape? ' + (rect instanceof Shape)); // true
rect.move(1, 1); // выведет 'Фигура переместилась.'

```


// Немного надоедает использовать .call каждый раз. Может воспользоваться bind? 
// Точно! Давайте привяжем функцию call к контексту slice. 

```js
slice = Function.prototype.call.bind(Array.prototype.slice);
```
 // Теперь slice использует первый аргумент в качестве контекста 
 
```js 
slice([1,2,3], 0, 1); // => [1]
```

**Полезное чтиво**

1. Зачем использовать Object.create() ?
https://stackoverflow.com/questions/15304318/javascript-inheritance-why-use-object-create

2. Чем работа через прототип отличается от работы через конструктор?
  http://stackoverflow.com/questions/8433459/js-why-use-prototype

  http://stackoverflow.com/questions/1948042/reason-for-using-prototype-in-javascript

3. Почему прототипное наследование действительно важно
http://aaditmshah.github.io/why-prototypal-inheritance-matters

4. Преимущества прототипного наследования перед классическим
http://stackoverflow.com/questions/2800964/benefits-of-prototypal-inheritance-over-classical?rq=1

**Практика:**

1.	Есть квадрат. Нужно сделать его прототипом круга
2.	Сделать массив кругов и квадратов. В цикле вывести их на экран
