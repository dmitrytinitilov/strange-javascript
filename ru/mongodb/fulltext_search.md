#Fulltext search

Полнотекстовый поиск на MongoDB


https://code.tutsplus.com/ru/tutorials/full-text-search-in-mongodb--cms-24835


```js
db.articles.find( { $text: { $search: "\"coffee shop\"" } } )
```