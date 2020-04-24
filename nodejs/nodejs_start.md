# NodeJS Старт

Нам понадобится NodeJS https://nodejs.org/en/ и NPM https://www.npmjs.com/

Для проверки установки вбейте в командную строку

```cli
node -help
```

и

```cli
npm -version
```
Обе эти команды должны срабатывать в любой директории на компьютере. Если же нет, то Вам нужно настроить переменные среды. Правый клик на "Мой компьютер" -> Дополнительные параметры -> Вкладка "Дополнительно" -> Переменные среды -> Нам нужна переменная Path

В Path через точку с запятой добавляем путь, где лежит nodejs и данные npm. У меня это _C:\nodejs\_ и _C:\Users\Tinitilov\AppData\Roaming\npm_ соответственно  


Создаем файл hello.js

```js
var message = "Hello World";
console.log(message);
```

переходим в папку с этим файлом и запускаем его

```cli
node hello.js
```

В консоль должно вывестись Hello World

Теперь попробуем запустить простой локальный сервер. Создадим server.js с таким наполнением

```js
var http = require('http');

var server = http.createServer(function(req, res) {
  res.writeHead(200);
  res.end('Hello Http');
});

server.listen(8080);
```

Для запуска пишем в командной строке

```cli
node server.js
```

Если всё хорошо, у нас не должно быть ошибок. Окошко с запущенным nodejs закрывать не нужно. Проверим запуск сервера в браузере. Пропишем в адресной строке

```cli
localhost:8080
```

Чтобы остановить запущенный nodejs-сервер из командной строки пишем process.exit(0) или Ctrl+Break или Ctrl+C


Запустим сервер, который будет выводить сколько раз был запущен данный сайт

```js
var http = require('http');
var i=0;

http.createServer(function (request, response) {
    i++;   
    response.write("Page was opened "+i+" times");
    response.end();
}).listen(8080);
```

В данном случае счетчик увеличивается на 2, за счет того, что браузер посылает запрос на получение страницы и favicon 



**Подборка материалов**
http://stackoverflow.com/questions/2353818/how-do-i-get-started-with-node-js
