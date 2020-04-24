# Переменные

Переменная в JavaScript оформляется с помощью конструкции var

```js
var x=5;
```
Если мы хотим увеличить значение переменной с целым числом, то мы можем это сделать вот так

```js
var x = 7;
x=x+1;
console.log(x);// 8
```

**Hoisting**

Речь идет о том, что если мы присваиваем переменной значение в коде, то она будет определена и выше, но со значением Undefined

```js
console.log(x);// Undefined

var x = 5;
```

1. О Hoisting в JavaScript
https://habrahabr.ru/post/127482/

2. ES2015 на пальцах. var, let, consthttps://medium.com/@vkozulya/es2015-%D0%BD%D0%B0-%D0%BF%D0%B0%D0%BB%D1%8C%D1%86%D0%B0%D1%85-var-let-%D0%B8-const-d194b902cfc0

3. Разница между var и let на простеньких примерах
https://www.geeksforgeeks.org/difference-between-var-and-let-in-javascript/