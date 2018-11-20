#Работа с POST-параметрами

**bodyParser**

Для начала нужно будет подключить bodyParser

http://stackoverflow.com/questions/24330014/bodyparser-is-deprecated-express-4

```js
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({
  extended: true
}));
```

**Обработка POST-запроса**

```js
app.post('/check',function(req,res){

  console.log(req.body.code);
  //обработка POST-параметра code

})
```

**Установка header'a**

http://stackoverflow.com/questions/23751914/how-can-i-set-response-header-on-express-js-assets

**Перенаправление**

Проблема POST-параметров в том, что при перезагрузке страницы, пользователю выведется "пугающее" сообщение, о том, что введенная им информация будет повторно использована.

Не стоит оставлять пользователя в таком положении и следует перенаправить его на новую страницу. По пути POST-параметры будут потеряны, что даст возможность пользователю нормально перегружаться.

Для перенаправления используем res.redirect

```js
res.redirect('/customers/');
```

http://stackoverflow.com/questions/22677940/difference-between-location-and-redirect-in-node-js


**Практика:**

1. Есть форма для ввода логина-пароля. Нужно отправить данные методом POST и проверить их правильность