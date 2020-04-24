# MongoDB CRUD

https://mongodb.github.io/node-mongodb-native/api-generated/collection.html


**insert**

```js
collection.insertOne({hello:'world'});
```

При добавлении записи в callback-функцию при завершении будет передан параметр, содержащий добавленный документ

```js
collection.insertOne(objectToInsert, function(err,docsInserted){
    console.log(docsInserted);
});
```

Из него можно будет получить, например id добавляемого документа

В случае варианта с await

```js
let insertedPicture = await picturesCollection.insertOne({name:req.files.photo.name,type:'basic'});
```

При этом в объекте, который нам вернут будет свойство insertedPicture c id нужной нам картинки

insertedPicture.insertedId

**insertMany**

```js
try {
   db.products.insertMany( [
      { item: "card", qty: 15 },
      { item: "envelope", qty: 20 },
      { item: "stamps" , qty: 30 }
   ] );
} catch (e) {
   print (e);
}
```



**Пример Read запроса**

```js
user.find( { login:'admin' } );
```

Вариант с условиями

```js
products.find( { qty: { $gt: 25 } }, { item: 1, qty: 1 } )
```

Если мы используем find, то нам могут вернуть несколько значений. Пройтись по ним можно через cursor

```js
products.find().toArray(function(err, items) {
  console.log(items);
  for (i=0;i<items.length;i++) {
    res.write((items[i]._id).toString());
  }
  res.end();
  db.close();
})          
```

Вариант через await


```js
items = await products.find().toArray(); 
console.log(items);
for (i=0;i<items.length;i++) {
    res.write((items[i]._id).toString());
}
res.end();
```


Очень подробно про find запросы
https://habrahabr.ru/post/134590/


**findOne**

Для одиночных запросов подходит findOne
https://docs.mongodb.com/manual/reference/method/db.collection.findOne/

```js
item = await db.bios.findOne(
   { contribs: 'OOP' },
   { _id: 0, 'name.first': 0, birth: 0 }
)
```

Второй параметр { _id: 0, 'name.first': 0, birth: 0 }
означает, что мы не берем данные поля в выдачу.


**Пример Update запроса**

Первый параметр задает запрос, по которому выбираются записи. Второй параметр задает вариант новой записи, которая придет на замену старой.


Если нам не нужна замена старой записи, а просто ее модификация, то нужно использовать параметры $inc и $set. $inc - увеличивает указанные поля на указанные значения. $set - устанавливает указанным полям новые значения, неуказанные поля остаются без изменения.

```js
books.update(
   { _id: 1 },
   {
     $inc: { stock: 5 },
     $set: {
       item: "ABC123",
       "info.publisher": "2222",
       tags: [ "software" ],
       "ratings.1": { by: "xyz", rating: 3 }
     }
   }
)

```

Если же на нам нужно добавить поле к уже существующим записям, то нужно добавить параметры upsert:false и multi:true

```js

replies.update({_id:items[i]._id},
               {$set:{answer_num:ans_num}},
               { upsert: false, multi: true }

```

**Пример Delete запроса**

```js
products.remove( { qty: { $gt: 20 } }, true )
```
true говорит о том, что мы удаляем одну запись

Удаление элемента по его id
```js
var ObjectId = require('mongodb').ObjectID;

test_users.remove( {"_id": ObjectId("4d512b45cc9374271b02ec4f")});
```

Получение информации по структуре БД
```js
users.findOne({_id:ObjectId(...)})
```

**Полезное чтиво:**

1. Что выбрать множественные коллекции или вложеные документы
http://openmymind.net/Multiple-Collections-Versus-Embedded-Documents


**Практика:**

1. Реализуйте гостевую книгу. То есть, есть форма для добавления комментариев. Под ней выводятся сами комментарии. 
