#ES6 Classes

Классы являются синтаксическим сахаром, то есть их можно преобразовать в код на ECMAScript5. Чтобы посмотреть как это происходит можно воспользоваться Babel'ем.
https://babeljs.io/repl/


```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

**Наследование классов**

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(this.name + ' издает звук.');
  }
}

class Dog extends Animal {
  speak() {
    console.log(this.name + ' лает.');
  }
}

var d = new Dog('Митци');
d.speak();
```
**Полезное чтиво:**

1. https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Classes

**Практика:**
1. Сделать класс прямоугольника, в котором хранится ширина, высота, фоновый цвет.


