# #Создание простейшего файл-сервера

Создадим файл страницы

index.html

```html
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>NodeJS - это серверный javascript</title>
</head>

<body>
    NodeJS - это серверный javascript.
</body>
</html>
```

Добьемся,чтобы при запросе к серверу у нас открывался файл index.html . Нам понадобится модуль для работы с файлами fs 

server.js

```js
var http = require('http');
var fs = require('fs');

http.createServer(function (request, response) {
    fs.readFile('index.html', function (err, data){
        if (err) {
            response.end("File wasn't found");
        }
        response.end(data);
    });
}).listen(8007);
```

**Дополнительные материалы:**
https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/

http://ru.code-maven.com/http-client-request-in-nodejs

**Практика:**

1. Создайте трехстраничный сайт с навигационным меню