# Паттерн модуль

Паттерн модуль является дальнейшим развитием замыканий. Только вместо одной функции, возвращается несколько функций объединенных в объект. При это данные внутри объекта являются открытыми\(public\), данные внешней функции являются закрытыми для внешнего использования\(private\), но по прежнему доступны для методов возвращаемого объекта.

```js
var obj= (function() {

    var a=5;
    var b=7;

    return {
        sum:function() {
            return a+b;
        },
        mult: function() {
            return a*b;
        }
    }

})()

console.log(obj.mult());
console.log(obj.a);
```

Допишем наш модуль

```js
var obj= (function() {

    var a=5;
    var b=7;
    var super_kvadrat = function() {
        return a*a+b*b;
    }

    return {
        sum:function() {
            return a+b;
        },
        mult: function() {
            return a*b;
        },

        sumOfSquares:function() {
            return super_kvadrat();
        }
    }
})()

console.log(obj.mult());
console.log(obj.a);
console.log(obj.sumOfSquares());
console.log(obj.super_kvadrat());
```

```js
var weekDay = (function() {
  var names = ["Понедельник", "Вторник", "Среда", "Четверг", "Пятница", "Суббота", "Воскресенье"];
  return {
    name: function(number) { return names[number]; },
    number: function(name) { return names.indexOf(name); }
  };
})();
```

Можно пойти дальше и не генерировать объект внутри внешней функции, а создавать его снаружи \(объект weeDay\), и передавать ссылку на него через параметр внешней функции \(exports\). Входе выполнения внешней функции изначально пустой объект exports наполняется методами.

```js
(function(exports) {
  var names = ["Понедельник", "Вторник", "Среда", "Четверг", "Пятница", "Суббота", "Воскресенье"];

  exports.name = function(number) {
    return names[number];
  };
  exports.number = function(name) {
    return names.indexOf(name);
  };
})(this.weekDay = {});

console.log(weekDay.name(weekDay.number("Saturday")));
```

**Дополнительные материалы:**

1. [https://medium.freecodecamp.com/javascript-modules-a-beginner-s-guide-783f7d7a5fcc](https://medium.freecodecamp.com/javascript-modules-a-beginner-s-guide-783f7d7a5fcc)

2. Эволюция JavaScript модулей   
   [https://habrahabr.ru/company/yandex/blog/192874/](https://habrahabr.ru/company/yandex/blog/192874/)

3. Путь JavaScript модуля  
   [https://habrahabr.ru/post/181536/](https://habrahabr.ru/post/181536/)

**Практика:**

1. Сделать модуль-галерею. Массив картинок -  закрытые данные. Есть три паблик метода: добавление картинки в массив, метод, который выводит i-ю картинку, метод который выводит всю галерею.



