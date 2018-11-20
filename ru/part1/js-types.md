# \# Типы данных в JavaScript

**String**

```
  var a = 'Hello';

  var b = "World!";

  var c = a+' '+b; // Hello World!
```

**Number**

_Integer_

```
  parseInt
  NaN (Not a number)
  Inf (Infinity)
```

_Float_

```js
      var x = 0.1 * 0.2;
      document.write(x);
```

0.02000000000004

**Boolean**

true      1,2,-1,'0'  
  false     0

**Objects**

**NULL**

В JavaScript есть элементы, которые мы храним по ссылке, но ссылочного типа нет. Это вынуждает выделять целый тип под ссылки, которые никуда не ведут

**Undefined**

Определенная переменная, значение которой не задано получает значение undefined.

```js
  var x;
  console.log(x); //undefined
```

**Подробнее о NULL и Underfined**  
[http://frontender.info/exploring-the-abyss-of-null-and-undefined-in-javascript/](http://frontender.info/exploring-the-abyss-of-null-and-undefined-in-javascript/)

**typeof**

**Преобразование типов**  
[https://habrahabr.ru/post/312172/](https://habrahabr.ru/post/312172/)

Интересная заметка об особенностях JavaScript  
[http://programmers-notes.blogspot.com/2012/02/javascript.html](http://programmers-notes.blogspot.com/2012/02/javascript.html)

**Практика:**

1. Получаем два числа через prompt. Выводим их сумму.


