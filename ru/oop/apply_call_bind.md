# apply,call,bind

http://habrahabr.ru/post/199456/

**Еще раз о контексте вызова**

```js
var a=5;

function func() {
   console.log(this.a);
}
****
func(); // 5

var obj = {a:7};
obj.func = func;

obj.func(); // 7
```
**apply , call**

// Создадим простой объект, чтобы использовать его в качестве контекста 
```js
var context = { c: 2 };

function median (a,b) { return (a+b)/this.c; }
median(5,7); //error

median.call(context,5,7); // 6

median.apply(context,[5,7]);//6

//аналогично
context.func = median;
context.func(5,7)


var bound_median = median.bind(context); 

bound_median(5,7);//6
```

**bind**

```js
this.x = 9;
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var getX = module.getX;
getX(); // 9, поскольку в этом случае this ссылается на глобальный объект

// создаём новую функцию с this, привязанным к module
var boundGetX = getX.bind(module);
boundGetX(); // 81
```

**Получение функции с новым набором параметров
**

// // Теперь давайте немного усложним 
// // В Array.prototype есть замечательный метод slice. 
// При вызове на массиве он возвращает копию массива 
// от начального индекса до конечного (исключительно)
```js
[1,2,3].slice(0,1); 
// => [1] 
// Мы берем slice и присваиваем его локальной переменной 
var slice = Array.prototype.slice;
 // slice теперь оторван от контекста. Из-за того, что Array.prototype.slice
 // работает с данным ему контекстом «this», метод больше не работает
slice(0, 1); // => TypeError: can't convert undefined to object 
slice([1,2,3], 0, 1); // => TypeError: ... // Но мы можем использовать apply и call, они позволяют нам передавать нужный контекст 
slice.call([1,2,3], 0, 1); // => [1] // Apply работает как call, но принимает аргументы в виде массива 
slice.apply([1,2,3], [0,1]); // => [1]
```

// Немного надоедает использовать .call каждый раз. Может воспользоваться bind? 
// Точно! Давайте привяжем функцию call к контексту slice. 
```js
var slice = Array.prototype.slice;
var call_func = Function.prototype.call;

big_slice =call_func.bind(slice);


big_slice = Function.prototype.call.bind(Array.prototype.slice);
 // Теперь slice использует первый аргумент в качестве контекста 
big_slice([1,2,3], 0, 1); // => [1]
```

**Функциональное наследование**

https://learn.javascript.ru/functional-inheritance


**Дополнительное чтиво:**

Функция bind своими руками
http://jsraccoon.ru/interview-bind


**Практика:**

1. Превратить метод Draw из предыдущего раздела в функцию, которая получает на вход объект круга и отрисовыввает его.

2. Есть функция, которая считает сумму своих аргументов. На ее основе получить функцию, которая принимаем на вход массив и считает сумму его элементов.