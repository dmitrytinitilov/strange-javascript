# Загрузка файла на NodeJS сервер, используя Express


**Модуль express-fileupload**

https://www.npmjs.com/package/express-fileupload

Нам необходимо подключить модуль

```js
var fileUpload = require('express-fileupload');

app.use(fileUpload({}));
```

Далее нам нужна форма с enctype="multipart-formdata"

```js
res.write('<form action="/get_file" method="POST" enctype="multipart/form-data" >');
   res.write('<input type="file" name="avatar">');
   res.write('<input type="submit">');
res.write('</form>');
```

Если у нашего input'a c type=file ыбл name avatar,то данные по файлу будут доступны в req.files.avatar

Поскольку nodejs копирует файлы в свою локальную директорию, нам небходимо перенести их в нужную нам папку

```js
req.files.avatar.mv('public/pics/'+req.files.avatar.name);
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
    res.write('<form action="/get_file" method="POST" enctype="multipart/form-data" >');
  		res.write('<input type="file" name="avatar">');
   		res.write('<input type="submit">');
   	res.write('</form>');
   	res.end();
})

app.post('/get_file', function(req, res) {
  req.files.avatar.mv('public/pics/'+req.files.avatar.name);
  res.end(req.files.avatar.name);
  console.log(req.files.avatar); // the uploaded file object
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

**Практика:**

1. Есть страница, на которой выводятся все загруженные фотографии. Сделать, чтобы у пользователя была возможность удалить указанную им фотографию (рядом с каждой картинкой, есть кнопка удалить)