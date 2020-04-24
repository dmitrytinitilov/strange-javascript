# Limit,skip,count,sort


**limit,skip**

```js
db.unicorns.find().sort({weight: -1}).limit(2).skip(1)
```

http://stackoverflow.com/questions/22441482/order-and-limit-results-in-a-query-with-a-callback

```js
myModel.find(filter)
       .limit(pageSize)
       .skip(skip)
       .sort(sort)
       .toArray(callback);
```
или такой вариант

```js
myModel.find(filter, {sort: {created_at: -1}, limit: 10}, function(err, items){
});
```

Обработка результата

```js

var found_people_promise = people_collection.find().limit(-1).skip(rnd).next();        

found_people_promise.then(function(people){
  db.close();
  console.log(people);
  res.end();
}, function(err) {
  console.log('Find random people error');
  res.end();
})
```

**Подсчет количества элементов в коллекции**


https://docs.mongodb.com/manual/reference/method/db.collection.countDocuments/

```js
db.collection.countDocuments()
```

**Сортировка**

```js
db.collection.find({ ... spec ... }).sort({ key: 1 })
```
где 1 - сортировка по возрастанию -1 сортировка по убыванию.

вариант через только через find

```js
db.collection.find( { $query: {}, $orderby: { columm : -1 } } )
```

**Практика:**

1. Сделать пагинацию на сайте
2. Вывести самый дорогой товар