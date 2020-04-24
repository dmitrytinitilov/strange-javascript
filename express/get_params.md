#GET-параметры

https://scotch.io/tutorials/use-expressjs-to-get-url-and-post-parameters

http://stackoverflow.com/questions/20089582/how-to-get-url-parameter-in-express-node-js

 ?tagId=5 use req.query

```js
app.get('/p', function(req, res) {
  res.send("tagId is set to " + req.query.tagId);
});
```

для ЧПУ

```js
app.get('/p/:tagId', function(req, res) {
  res.send("tagId is set to " + req.params.tagId);
});
```

**Практика:**

1. Сделать скрипт, который находит сумму двух чисел
2. Сделать трехстраничный сайт