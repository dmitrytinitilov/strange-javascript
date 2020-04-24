# Загрузка файла на NodeJS сервер, используя Express


**Модуль express-fileupload**

https://www.npmjs.com/package/express-fileupload

Нам необходимо подключить модуль

```cli
npm i express-fileupload
```


```js
var fileUpload = require('express-fileupload');

app.use(fileUpload({}));
```

Далее нам нужна форма с enctype="multipart-formdata"

```js
  res.write('<form action="/upload" method="POST" enctype="multipart/form-data" >');
  res.write('<input type="file" name="photo">');
  res.write('<input type="submit">');
  res.write('</form>');
```

или если у Вас установлен pug, то можно сделать вот такой код

```js
form(action='/upload' method='POST' enctype='multipart/form-data')
    input(type='file' name='photo')
    input(type='submit')
```

Если у нашего input'a c type=file был name avatar,то данные по файлу будут доступны в req.files.photo

Поскольку nodejs копирует файлы в свою локальную директорию, нам небходимо перенести их в нужную нам папку

```js
req.files.photo.mv('public/pics/'+req.files.photo.name);
```

Полный код

```js
var express = require('express');
var fileUpload = require('express-fileupload');
var app = express();

app.use(fileUpload({}));

app.use(express.static('public'));

app.get('/', function (req, res) {
  res.send('Hello World');
})

app.get('/form', function (req, res) {
  res.setHeader('content-type', 'text/html;charset=utf-8');
  res.write('<form action="/upload" method="POST" enctype="multipart/form-data" >');
  res.write('<input type="file" name="photo">');
  res.write('<input type="submit">');
  res.write('</form>');
  res.end();
})

app.post('/upload', function(req, res) {
  req.files.photo.mv('public/pics/'+req.files.photo.name);
  res.end(req.files.photo.name);
  console.log(req.files.photo); // the uploaded file object
});

var server = app.listen(8081, function () {

  var host = server.address().address
  var port = server.address().port

  console.log("Example app listening at http://%s:%s", host, port)

})

```

**Более ранний вариант через multer**

https://howtonode.org/really-simple-file-uploads

https://www.npmjs.com/package/multer


Для реализации понадобится установка модуля multer

```bash
npm i multer
```

И создание папки uploads

```js
var express = require('express');
var app = express();

var fs = require('fs');

var multer  = require('multer')
var upload = multer({ dest: 'uploads/' })

app.get('/', function (req, res) {
   res.setHeader('content-type', 'text/html;charset=utf-8');
   res.write('<link rel="stylesheet" href="css/style.css">');
   res.write('<form action="/upload" method="POST" enctype="multipart/form-data">');
      res.write('<input type="file" name="avatar">');
      res.write('<input type="submit">');
   res.write('</form>');
   res.end();
})

app.post('/upload', upload.single('avatar'), function (req, res, next) {
	console.log(req.file);

	fs.rename(req.file.path, 'uploads/'+req.file.originalname, function (err) {
 		if (err) throw err;
  		console.log('renamed complete');
	});

	res.end('Gotcha');
  // req.file is the `avatar` file
  // req.body will hold the text fields, if there were any
})


var server = app.listen(8081, function () {

  var host = server.address().address
  var port = server.address().port

  console.log("Example app listening at http://%s:%s", host, port)

})

```

**Генерация случайной строки**


```js
var crypto = require('crypto');

var id = crypto.randomBytes(20).toString('hex');
```

**Практика:**

1. Есть страница, на которой выводятся все загруженные фотографии. Сделать, чтобы у пользователя была возможность удалить указанную им фотографию (рядом с каждой картинкой, есть кнопка удалить)