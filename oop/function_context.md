#Контекст вызова функции

**Контекст вызова функции**

```js
var person = {
  name:'Petya',
  getName:function() {
    return this.name;
  }
}

var person2 = {
  name:'Vasya'
}

person2.getName = person.getName;

person2.getName(); // ?
```

**this и куда он указывает**

```js
var name = 'Strange';

var person = {
  name:'Petya',
  getName:function() {
    return this.name;
  }
}

//скопируем метод в переменную
var getThatName = person.getName;

//вызовем получившуюся функцию
var result = getThatName();

console.log(result);//?

console.log(this.name);//?

console.log(this);//?
```

**self**


**Цепочки вызовов**

https://learn.javascript.ru/task/chain-calls



**Практика**

1. Есть кнопка, которая при нажатии генерирует круги. Круги при нажатии меняют цвет(мигалка). Оформить все переменные и методы внутри объекта.

**Интересное чтиво:**

1. Очень подробно о this
https://zellwk.com/blog/this/