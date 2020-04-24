#Pug

Установим Pug в наш проект

```
npm install pug
```

Создадим базовый шаблон в папке views

```jade
html
    head
	link(href='/css/style.css' rel='stylesheet')
    body Hello World!
```

Подключим pug к проекту

```js
pug = require(pug);

app.set('view engine', 'pug');

app.get('/test_render',function(req,res){
	res.render('test_render',{});
})
```

**Передача переменной в шаблон**

Попробуем передать переменную в test_render.pug

```js
app.get('/test_render',function(req,res){
	res.render('test_render',{message:'big start starts here'});
})
```

Создаем test_render.pug

```jade
html
    head
	link(href='/css/style.css', rel='stylesheet')
    body Hello World!
	h1= message
```

**Подключение CSS к шаблону**

```jade
head
  title First Express App
  link(href='/css/style.css' rel='stylesheet')
```

**Пример простой формы на Pug**

```jade
form(method=GET action='/authorize')
	input(name='login' placeholder='login')
	input(name='password' placeholder='password')
	input(type='submit' value='залогиниться')
```

или

```jade
input(name='caption' placeholder='caption')
textarea(name='description' placeholder='description')
button(class='submit_button') Добавить комментарий
```

**Передача параметра в value input'a**

```jade
input(type="text" name="date" value=viewpost.date)
```


**Работа с массивами внутри Pug**

Передаем переменную listOfElements и работаем с ней через each

```jade
ul
each element in listOfElements
    li= element.name
```


**Наследование шаблонов в Pug**

https://pugjs.org/language/inheritance.html

https://pugjs.org/language/includes.html

Пример с официального сайта

```jade
//- index.pug
doctype html
html
  include includes/head.pug
  body
    h1 My Site
    p Welcome to my super lame site.
    include includes/foot.pug
```

```jade
//- includes/head.pug
head
  title My Site
  script(src='/javascripts/jquery.js')
  script(src='/javascripts/app.js')
```

```jade
//- includes/foot.pug
footer#footer
  p Copyright (c) foobar
```

**Передача параметра в include**

https://stackoverflow.com/questions/37936197/jade-include-with-parameter

**Условия в pug**

https://pugjs.org/language/conditionals.html

```jade
if hash_obj.login
    h1= hash_obj.login
else
    a(href="/login")
        img(src='icons/key_icon.png')

```

**Встроенный script**

```jade
script.
  var users = !{JSON.stringify(users).replace(/<\//g, "<\\/")}
```



**Пример с нахождением суммы двух чисел**

Шаблон формы sum_form.pug

```jade
form(method=GET action='/get_sum')
    input(name='a' placeholder='a')
    input(name='b' placeholder='b')
    input(type='submit' value='сумма')
```


Само приложение app.js

```js
var express = require('express');
var app = express();

app.set('view engine','pug');

app.get('/',function(req,res){
	res.render('sum_form');
})

app.get('/get_sum',function(req,res){
	var sum = parseInt(req.query.a) + parseInt(req.query.b);
	sum = sum+'';
	res.end(sum);
})

var server = app.listen(8080,function(){

	console.log('Server got the power');

})
```

**Интересное чтиво:**

1. Полезная статья о pug, которая заставит Вас улыбнуться
https://codepen.io/mimoduo/post/learn-pug-js-with-pugs

2. Использование шаблонизаторов в Express
http://expressjs.com/ru/guide/using-template-engines.html

3. Введение в Jade
https://webapplog.com/jade/

4. Handlebars
https://www.packtpub.com/books/content/using-handlebars-express

5. Использование шаблонизаторов в express
https://webapplog.com/jade-handlebars-express/


**Практика:**

1. Есть массив имен - выводим их ввиде списка
2. Создаем трехстраничный сайт с навигационным меню сверху. Навигационное меню выносим в отдельный шаблон