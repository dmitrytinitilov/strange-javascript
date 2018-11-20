# Promises


https://stackoverflow.com/questions/36490803/javascript-promises-and-settimeout

```js

function use_after_complete() {
    console.log('You got it!');
}

function later(delay) {
    return new Promise(function(resolve) {
        setTimeout(resolve, delay);
    });
}

var prms = later(2000);
prms.then(use_after_complete);
```

**Цепочка промисов**


```js
function a() { 
    return new Promise(function (resolve, reject) { 
        resolve("hi from a!");
    });
}

function b() { 
    return new Promise(function (resolve, reject) { 
        setTimeout(function () { 
            resolve("hi from b!");
        }, 5000);
    });
}

function c() { 
    return new Promise(function (resolve, reject) { 
        setTimeout(function () { 
            resolve("hi from c!");
        }, 1000);
    });
}

a().then(function (resultFromA) {
    console.log("a() responded with: " + resultFromA);
    return b(); // return 
}).then(function (resultFromB) { 
    console.log("b() responded with: " + resultFromB);
    return c(); // return
}).then(function (resultFromC) { 
    console.log("c() responded with: " + resultFromC);
});
```

**Полезное чтиво:**

1. MDN о промисах в es6
https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise

2. Огромное количество вариантов использования промисов
http://2ality.com/2014/10/es6-promises-api.html

3. Еще варианты использования
http://exploringjs.com/es6/ch_promises.html

4. Создание цепочек вызовов в JS  
https://html5hive.org/how-to-chain-javascript-promises/