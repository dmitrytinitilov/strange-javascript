# Создаем чат на NodeJS

https://habrahabr.ru/post/200866/

Чат на Socket.io
https://habrahabr.ru/post/127525/

```js
// создаем сервер
var WebSocketServer = require('ws').Server,
	wss = new WebSocketServer({port: 9000});

// соединение с БД
var MongoClient = require('mongodb').MongoClient,
	format = require('util').format;   

var userListDB, chatDB;

// подсоединяемся к БД
MongoClient.connect('mongodb://127.0.0.1:27017', function (err, db) {
	if (err) {throw err}
	
	// записываем ссылки на таблицы (коллекции) в глобальные переменные
	userListDB = db.collection('users');
	chatDB = db.collection('chat');
});
```