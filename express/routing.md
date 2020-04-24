#Роутинг на Express


```js
app.get('/p/:tagId', function(req, res) {
  //то есть параметр tagId уйдет в req.params.tagId
  res.send("tagId is set to " + req.params.tagId);
});
```

**express.Router**


```js
var express = require('express');
var router = express.Router();

// middleware that is specific to this router
router.use(function timeLog(req, res, next) {
  console.log('Time: ', Date.now());
  next();
});
// define the home page route
router.get('/', function(req, res) {
  res.send('Birds home page');
});
// define the about route
router.get('/about', function(req, res) {
  res.send('About birds');
});

module.exports = router;
```

Потом мы можем загрузить модуль маршрутизации в приложение:

```js
var birds = require('./birds');
...
app.use('/birds', birds);
```

**Полезное чтиво:**

1. Подробно о вариантах роутинга на Express     
http://expressjs.com/ru/guide/routing.html