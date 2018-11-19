**Установка Cookies**

Хорошая статья по установке Cookies на Express
https://www.codementor.io/nodejs/tutorial/cookie-management-in-express-js

Нам понадобится модуль cookie-parser

Подробнее о модуле можно прочитать по ссылке
https://www.npmjs.com/package/cookie-parser

**Подключение модуля cookie-parser**

```
npm install cookie-parser
```

После установки подключим его в наш код

```js
var express = require('express');
var cookieParser = require('cookie-parser');

var app = express();
app.use(cookieParser());
```

**Установка куки**

Далее в коде нашего приложения попробуем установить нашу куку

```js
app.get('/cookie',function(req, res){
     res.cookie('cookie_name' , 'cookie_value').send('Cookie is set');
});
```

**Считывание куки**

```js
app.get('/', function(req, res) {
  console.log("Cookies :  ", req.cookies);
  
  console.log("Cookies :  ", req.cookies.cookie_name);
});
```

**Установка куки на длительный срок**

вариант со сроком годности

```js
res.cookie(name , 'value', {expire : new Date() + 9999});
```

вариант с временем жизни. Обратите внимание, что 9999 - это миллисекунды, то есть это всего лишь 10 секунд!

```js
res.cookie(name, 'value', {maxAge : 9999});
```

**Удаление cookie**

```js
app.get('/clearcookie', function(req,res){
     res.clearCookie('cookie_name');
     res.send('Cookie deleted');
});
```


**Практика:**

1. Показывать пользователю, сколько раз он загрузил страницу
2. Есть форма для ввода логина, пароля с флажком "запомнить меня". Если пользователь ввел данные правильно, мы должны "залогинить" его, то есть установить куку с каким-то специальными значением. Должна быть отдельная страница, на которой мы можем проверить залогинен ли пользователь.