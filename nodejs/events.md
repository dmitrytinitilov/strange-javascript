# #События

events
eventEmitter

https://www.sitepoint.com/nodejs-events-and-eventemitter/
http://www.hacksparrow.com/node-js-eventemitter-tutorial.html

```js
var events = require('events');
var eventEmitter = new events.EventEmitter();

eventEmitter.on('myCustomEvent', function(arg1,arg2)) {
  console.log(arg1+arg2);
}

setTimeout(function() {
  eventEmitter.emit('myCustomEvent','String1','and String2');
},2000);
```


```js

const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
  console.log('an event occurred!');
});
myEmitter.emit('event');

```


Дополнительные материалы:
https://www.youtube.com/watch?v=Fguk1wB9Ob8&index=12&list=PLYxzS__5yYQmHbpKMARP04F344zYRX91I

Практика:

1. Сделать, чтобы страница при каждом десятом запуске поздравляла пользователя. Использовать свое кастомное событие
2. Есть три чекбокса. Когда нажаты 2 чекбокса из 3 - поздравляем пользователя.
3. Проверка логина-пароля