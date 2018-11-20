# WebSockets

WebSocket'ы на express
https://hackernoon.com/nodejs-web-socket-example-tutorial-send-message-connect-express-set-up-easy-step-30347a2c5535

```cli
npm i express ws
```

Создаем app.js

```js
var express = require('express')
var ws = require('./ws')
var app = express()
app.get('/', function (req, res) {
   res.sendfile(__dirname + '/ws.html');
})
app.listen(3000, function () {
   console.log('Example app listening on port 3000!')
})
```

Создаем ws.js, который будет отвечать за WebSocket'ы

```js
var WebSocketServer = require('ws').Server,
wss = new WebSocketServer({port: 40510})
wss.on('connection', function (ws) {
  ws.on('message', function (message) {
    console.log('received: %s', message)
  })
  setInterval(
    () => ws.send(`${new Date()}`),
    1000
  )
})
```

Клиентская часть будет представлена ws.html

```html
<script>
var ws = new WebSocket('ws://localhost:40510');
// event emmited when connected
ws.onopen = function () {
    console.log('websocket is connected ...')
    // sending a send event to websocket server
    ws.send('connected')
}
// event emmited when receiving message 
ws.onmessage = function (ev) {
    console.log(ev);
}

</script>
```

Запускаем app.js и открываем консоль браузера. Если всё прошло успешно, то мы должны увидеть как у нас появляются новые сообщения со временем и датой.


**Поиск и удаление отвалившихся соединений**

```js
const WebSocket = require('ws');
 
const wss = new WebSocket.Server({ port: 8080 });
 
function noop() {}
 
function heartbeat() {
  this.isAlive = true;
}
 
wss.on('connection', function connection(ws) {
  ws.isAlive = true;
  ws.on('pong', heartbeat);
});
 
const interval = setInterval(function ping() {
  wss.clients.forEach(function each(ws) {
    if (ws.isAlive === false) return ws.terminate();
 
    ws.isAlive = false;
    ws.ping(noop);
  });
}, 30000);
```

**Полезное чтиво:**

1. О протоколе WebSockets и сравнение c http2
https://habr.com/company/ruvds/blog/342346/

2. Подробнее о модуле ws
https://www.npmjs.com/package/ws

3. http://hungtran.co/long-polling-and-websockets-on-nodejs/

4. http://stackabuse.com/node-js-websocket-examples-with-socket-io/

5. http://ahoj.io/nodejs-and-websocket-simple-chat-tutorial

**Практика:**

1. На клиентской стороне создаем кнопку, на которую можно кликать. Отображаем на ней общее количество кликов от всех пользователей.

2. Создаем чат, использующий WebSockets



