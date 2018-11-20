# Каррирование

Каррирование заменяет адаптер

```js
pow(i, j); 

function square(i) { 
	return pow(i, 2); 
} 
```

```js
function mul(a, b) {
  return a * b;
};

var double = mul.bind(null, 2); // контекст фиксируем null, он не используется
```

Говорят, что double является «частичной функцией» (partial function) от mul


Еще пример

```js
var greet = function(greeting, name) {
  console.log(greeting + ", " + name);
};
greet("Hello", "Heidi"); //"Hello, Heidi"
```

```js
var greetCurried = function(greeting) {
  return function(name) {
    console.log(greeting + ", " + name);
  };
};
```

```js
var greetHello = greetCurried("Hello");
greetHello("Heidi"); //"Hello, Heidi"
greetHello("Eddie"); //"Hello, Eddie"
```

В общем виде функция каррирования выглядит вот так

```js
function curry(func, a) {
	return function (b) {
	    return func(b,a);
	};
}
```


**Практика:**
1.	Получить из функции pow, функцию 2^n
2.	Получить из функции, которая рисует прямоугольник, функцию, которая рисует квадрат.
3.	Есть функция func(a,b) - сделать функцию x, которую можно вызывать x(a)(b), но ее действие было бы аналогичным
