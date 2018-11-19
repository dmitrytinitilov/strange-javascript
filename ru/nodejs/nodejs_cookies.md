# COFFEE nodejs cookies

**Работа с cookies на "нативном" NodeJS**

http://stackoverflow.com/questions/3393854/get-and-set-a-single-cookie-with-node-js-http-server

```js
var http = require('http');

//функция, которая позволяет распарсить куки
function parseCookies (request) {
    var list = {},
        rc = request.headers.cookie;
        //получаем строку кук
        
//проходимся по всем кукам
    rc && rc.split(';').forEach(function( cookie ) {
        var parts = cookie.split('=');
        list[parts.shift().trim()] = decodeURI(parts.join('='));
    });

    return list;
}


http.createServer(function (request, response) {

  // Разбираем куки. В массиве cookies ключами будут названия кук
  var cookies = parseCookies(request);

  // Кусок кода для записи кук
  response.writeHead(200, {
    'Set-Cookie': 'mycookie=test',
    'Content-Type': 'text/plain'
  });
  // Устанавливаем куку mycookie со значением test
  
  response.end('Hello World\n');
}).listen(8124);

console.log('Server running at http://127.0.0.1:8124/');

```

*Разница между max-age и expires*
http://mrcoles.com/blog/cookies-max-age-vs-expires/




**Вариант работы с COOKIES через express**

http://stackoverflow.com/questions/12240274/set-a-cookie-value-in-node-js

https://www.tutorialspoint.com/nodejs/nodejs_response_object.htm

https://www.codementor.io/nodejs/tutorial/cookie-management-in-express-js

Вариант с cookie-parser
https://github.com/expressjs/cookie-parser

```js
var express      = require('express')
var cookieParser = require('cookie-parser')

var app = express()
app.use(cookieParser())
```

**Практика:**

1. Сделать страницу, которая бы показывала количество своих загрузок пользователю.
2. Есть меню ввода логина-пароля. Сделать "залогинивание" пользователя(дописываем куку, если проверки пройдены)
3. Добавляем чекбокс "запомнить меня"
4. Есть серый блок и три цветных блока. При клике на цветной, серый блок окрашивается в цвет. При запуске кода заново серый блок окрашивается в последний выбранный цвет.

