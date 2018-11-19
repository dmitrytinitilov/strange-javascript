# Работа с бандлами

```cmd
npm i -g browserify
```

Установим jQuery с помощью npm

```cmd
npm i jquery
```

Создадим app.js и подключим к нему jQuery через require

```js

$ = require('jquery');

console.log($);

```

Соберем app.js в bundle.js

```cmd
browserify app.js -o bundle.js
```





**Полезное чтиво:**

1. Сборка проекта на Gulp и Browserify   
   [https://habrahabr.ru/post/251807/](https://habrahabr.ru/post/251807/)

2. Работа с jQuery через Broserify  
   [http://rkulla.blogspot.com/2014/04/using-browserify-with-jquery-backbonejs.html](http://rkulla.blogspot.com/2014/04/using-browserify-with-jquery-backbonejs.html)

3. [https://quickleft.com/blog/setting-up-a-clientside-javascript-project-with-gulp-and-browserify/](https://quickleft.com/blog/setting-up-a-clientside-javascript-project-with-gulp-and-browserify/)



