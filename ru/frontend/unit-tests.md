#Unit-тесты


http://metanit.com/web/nodejs/5.1.php

```js
var operations = require("./operations");
 
it("should multiply two numbers", function(){
     
    var expectedResult = 15;
    var result = operations.multiply(3, 5);
    if(result!==expectedResult){
        throw new Error(`Expected ${expectedResult}, but got ${result}`);
    }
});
```

Подключим какую-то assertion-library, например chai

```bash
npm i chai --save-dev
```

Подключим в наш test.js

```js
var assert = require('chai').assert
```

```js
describe("multitests", function() {

  function makeTest(x) {
    var expected = x * x * x;
    it("при возведении " + x + " в степень 3 результат: " + expected, function() {
      assert.equal(operations.pow(x, 3), expected);
    });
  }

  for (var x = 1; x <= 5; x++) {
    makeTest(x);
  }

});
```

http://chaijs.com/api/bdd/

```js
expect(function () {}).to.not.throw();
expect({a: 1}).to.not.have.property('b');
expect([1, 2]).to.be.an('array').that.does.not.include(3);
```


**Подробнее:**

1. https://learn.javascript.ru/testing

2. Виды тестирования на фронтенде
http://www.creativebloq.com/how-to/an-introduction-to-frontend-testing

