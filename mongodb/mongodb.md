# MongoDB Старт

Установка MongoDB под Ubuntu
https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/

Находим папку с файлом mongod.exe и пишем

```cli
mongod --dbpath D:\mongodb\data --port 27017
```

--port - задает порт, на котором будет работать mongodb. По умолчанию это 27017

--dbpath - задает путь к данным БД


Если запускаться с каким-то конфигурационным файлом

```cli
"C:\mongodb\bin\mongod.exe" --config "C:\mongodb\mongod.cfg"
```

Инсталляция через npm

```js
npm install mongodb
```

Тестируем подключение в nodejs на этой строчке
```js
var mongo = require('mongodb');
```

Создадим файл db.js подключения к БД

```js
module.exports = async function() {
	let MongoClient = require('mongodb').MongoClient;

	let database = await MongoClient.connect('mongodb://localhost:27017',{useNewUrlParser : true});

	return  database.db('yourdatabase');
}
 ```



Создадим файл server.js Пробуем добавить что-то в базу данных, а потом считать

```js
(async function() {

	try {

		var getDb = require('./db');
		db = await getDb();

		var collection = db.collection("simple_collection");
		collection.insertOne({hello:'world'});

		collection.findOne({hello:'world'}, function(err, item) {
			console.log(item);
		})

	} catch(e) {
		console.log(e);
	}	

})()

```

Вариант с await

```js
(async function() {

	try {

		var getDb = require('./db');
		db = await getDb();

		var collection = db.collection("simple_collection");
		await collection.insertOne({hello:'world'});

		item = await collection.findOne({hello:'world'});
		
		console.log(item);

	} catch(e) {
		console.log(e);
	}	

})()

```

Для сохранения соединения мы можем использовать переменную app.locals. Например

```js
(async () => {
	let getDb = require('./db');
	app.locals.db = await getDb();
})()
```


**Полезное чтиво:**

1. Вариант с подключением через async, выполнением запроса и закрытием соединения
https://stackoverflow.com/questions/47370487/node-js-mongodb-driver-async-await-queries

2. Организация проекта на NodeJS, MongoDb
  https://www.terlici.com/2015/04/03/mongodb-node-express.html
3. Организация соединения с MongoDb при работе с Express 
https://blog.mlab.com/2017/05/mongodb-connection-pooling-for-express-applications/

4. Минимануал по установке
http://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/?_ga=1.195041452.1278229924.1436390555



**Практика:**

1. Делаем гостевую книгу. Есть форма для добавления комментария. Под ней должны выводиться ранее добавленные комментарии.
