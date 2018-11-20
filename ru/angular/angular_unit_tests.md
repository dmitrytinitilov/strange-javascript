#Unit-тесты в Angular

**Быстрый старт**

Скачиваем standalone версию Jasmine
https://github.com/jasmine/jasmine/releases

Нам нужен файл SpecRunner.html, который лежит в корне.

Создаем свой hello.js

```js
function helloWorld() {
  return "Hello world!";
}
```

Подключаем его к SpecRunner.html . В нем же дописываем код

```js
describe("Hello world", function() {
  it("says hello", function() {
    expect(helloWorld()).toEqual("Hello world!");
  });
});
```

Запускаем и ищем строчку "Hello World says hello"

Давайте разберем, что происходит

В describe мы указываем описание самого теста.
it - дает описание того, что должно происходить в тесте
expect - запускает функцию, которую мы тестируем и метод для сравнения (в нашем примере toEqual)

Создание собственной функции сравнения

```js
function gimmeANumber() {
    var x = 4;
    return x;
}

describe('Hello world', function () {

    beforeEach(function () {
        jasmine.addMatchers({
            toBeDivisibleByTwo: function () {
                return {
                    compare: function (actual, expected) {
                        return {
                            pass: (actual % 2) === 0
                        };
                    }
                };
            }
        });
    });

    it('is divisible by 2', function () {
        expect(gimmeANumber()).toBeDivisibleByTwo();
        expect(5).not.toBeDivisibleByTwo();
    });

});

```

Пример взят с http://stackoverflow.com/questions/23986665/jasmine-2-0-test-with-a-custom-matcher-fails-undefined-is-not-a-function



**Дополнительные материалы:**

Пошаговое руководство для быстрого старта

https://evanhahn.com/how-do-i-jasmine/

Фикс примера с добавлением собственного matcher'a
http://stackoverflow.com/questions/23986665/jasmine-2-0-test-with-a-custom-matcher-fails-undefined-is-not-a-function

Введение в Jasmine

https://habrahabr.ru/post/167173/

Jasmine для NodeJS

https://github.com/jasmine/jasmine-npm
https://jasmine.github.io/2.5/node.html

http://stepansuvorov.com/blog/2012/10/jasmine-%D0%B8-%D1%8E%D0%BD%D0%B8%D1%82-%D1%82%D0%B5%D1%81%D1%82%D1%8B/

Unit-тесты с помощью Jasmine
https://docs.angularjs.org/guide/unit-testing

Jasmine, Karma
https://scotch.io/tutorials/testing-angularjs-with-jasmine-and-karma-part-1

**Практика:**

1. Сделать функцию, которая находит максимум из трех чисел. Написать как минимум три теста для тестирования.