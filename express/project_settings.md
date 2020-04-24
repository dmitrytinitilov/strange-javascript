# Настройка проекта


Загрузим модули

```cli
npm i express body-parser pug mongodb express-fileupload
```

Создадим файл db.js для поключения к базе данных

```js
module.exports = async function() {
	let MC = require('mongodb').MongoClient;

	let database = await MC.connect('mongodb://localhost:27017',{useNewUrlParser:true});

	return database.db('yourdatabase');
}

```

Добавим необходимые библиотеки

```js
const util = require('util');

const express = require('express');
const app = express();

const bodyParser = require('body-parser');
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({
	extended:true
}))

const fileUpload = require('express-fileupload');
app.use(fileUpload({}));

pug = require('pug');
app.set('view engine','pug');

app.use(express.static('public'));

(async () =>{
	let getDb = require('./db');
	app.locals.db = await getDb();
})()
```