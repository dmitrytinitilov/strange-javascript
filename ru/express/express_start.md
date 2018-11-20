# Основы Express

https://www.tutorialspoint.com/nodejs/nodejs_express_framework.htm

Установка
```
$ npm install express --save
```

```js
var express = require('express');
var app = express();

app.get('/', function (req, res) {
   res.send('Hello World');
})

var server = app.listen(8081, function () {

  var host = server.address().address
  var port = server.address().port

  console.log("Example app listening at http://%s:%s", host, port)

})
```

res.send() - заканчивает отдачу данных

Подробно о response object
https://www.tutorialspoint.com/nodejs/nodejs_response_object.htm

Подробно о request object
https://www.tutorialspoint.com/nodejs/nodejs_request_object.htm

**Строим файл-сервер на express**

```js
var express = require('express');
var app = express();

app.use(express.static('public'));

app.get('/', function (req, res) {
   res.send('Hello World');
})

var server = app.listen(8081, function () {

  var host = server.address().address
  var port = server.address().port

  console.log("Example app listening at http://%s:%s", host, port)

})
```

Если мы добавим картинку в директорию public, то сможем к ней обращаться через localhost:8081/picture.jpg

**Ответ содержимым файла**

Научимся отдавать файлы на запрос пользователя

```js
res.sendFile(__dirname+'path/to/your/file.html')
```

**Генерация файла построчно**

```js
app.get('/adduser',function (req,res){
	res.setHeader('content-type', 'text/html;charset=utf-8');
	res.write('<form action="adduser" method="GET">');
	res.write('<input type="text" name="username">');
	res.write('<input type="submit">');
	res.write('</form>');
	res.end();
})
```


**Полезное чтиво**

1. Мануал по Express
http://jsman.ru/express/

2. Подключение статических файлов
http://expressjs.com/ru/starter/static-files.html

3. Генерация проекта-заготовки на Express
https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/skeleton_website

4. Диспетчеры процессов под Express
http://expressjs.com/ru/advanced/pm.html


**Практика:**

1. Сделать галерею картинок. При клике на картинку, мы переходим на нее