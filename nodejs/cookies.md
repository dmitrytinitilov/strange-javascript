#Cookies

**Установка cookie**

http://stackoverflow.com/questions/3393854/get-and-set-a-single-cookie-with-node-js-http-server

```js
var http = require('http');

function parseCookies (request) {
    var list = {},
        rc = request.headers.cookie;

    rc && rc.split(';').forEach(function( cookie ) {
        var parts = cookie.split('=');
        list[parts.shift().trim()] = decodeURI(parts.join('='));
    });

    return list;
}


http.createServer(function (request, response) {

  // To Read a Cookie
  var cookies = parseCookies(request);

  // To Write a Cookie
  response.writeHead(200, {
    'Set-Cookie': 'mycookie=test',
    'Content-Type': 'text/plain'
  });
  response.end('Hello World\n');
}).listen(8124);

console.log('Server running at http://127.0.0.1:8124/');
```

**Expired/Max-age**

http://stackoverflow.com/questions/7374042/how-can-i-set-a-cookies-expiration-in-nodejs

http://www.connecto.io/blog/nodejs-express-how-to-set-multiple-cookies-in-the-same-response-object/

**Генерация хеша**

```js
require('crypto').randomBytes(48, function(err, buffer) {
  var token = buffer.toString('hex');
});
```

https://stackoverflow.com/questions/8855687/secure-random-token-in-node-js


**Практика:**

1. Установить куку. Проверить ее установку в браузере
2. Сделать страницу, которая подсчитывает сколько раз пользователь ее посетил
3. Есть круг. Пользователь выбирает цвет круга
4. Пользователь выбирает цвет и радиус круга. Сохраняем настройки в куках.
5. Сделать программу, которая запоминает пользователя