#Агрегация

Многим долгое время не хватало аналога конструкции JOIN из SQL в mongodb-запросах. Теперь у нас появилась агрегация в MongDb

**Конструкция $lookup**

Пример взят с сайта w3schools. Подробнее в ссылках внизу страницы.

```js
orders.aggregate([
    { $lookup:
      {
        from: 'products',
        localField: 'product_id',
        foreignField: '_id',
        as: 'orderdetails'
      }
    }
  ])
```

Подробнее:
https://docs.mongodb.com/manual/reference/operator/aggregation/lookup/

**Объединение нескольких коллекций**

В принципе мы можем сделать несколько $lookup'ов, но иногда нам нужно добраться до вложеных в объекты полей. Для этого нам нужно научиться модифицировать выбранные документы.


**$replaceRoot** - перемещает поля из вложенного поддокумента в корень
https://docs.mongodb.com/manual/reference/operator/aggregation/replaceRoot/

**mergeObjects** - объединение двух документов
https://docs.mongodb.com/manual/reference/operator/aggregation/mergeObjects/

**$project** - позволяет выбрать или убрать необходимые поля. Название поля с 1 выбирает его, с нулем убирает.
https://docs.mongodb.com/manual/reference/operator/aggregation/project/

```js
{   $lookup:
    {
        from: 'events',
	localField: 'event_id',
	foreignField: '_id',
	as: 'details'
    }
},
{
    $replaceRoot: { newRoot: { $mergeObjects: [ {$arrayElemAt: [ "$details", 0 ] }, "$$ROOT" ] } }
},
{ $project: { details: 0 } },
{
    $lookup:{
    from:'pictures',
    localField:'picture_id',					          foreignField: '_id',
    as:'pic_details'
}
}
```


**Полезное чтиво:**
1. Простой пример использования $lookup
https://www.w3schools.com/nodejs/nodejs_mongodb_join.asp
2. Хорошая презентация по $lookup в mongodb
https://www.slideshare.net/mongodb/doing-joins-in-mongodb-best-practices-for-using-lookup