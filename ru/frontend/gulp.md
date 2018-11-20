#gulp

Подробнее
https://golosay.net/gulp-setup-and-settings/

```cmd
npm init
```

```
npm install --save-dev gulp
```

Создадим gulpfile.js

```js
var gulp = require('gulp');
gulp.task('default', function() {
  // место для кода, который будет выполняться в задаче
});
```

**Сборка SASS**

```cmd
npm install gulp-sass --save-dev
```

```js
var gulp = require('gulp');
var sass = require('gulp-sass');
//Задача для сборки
gulp.task('sass', function () {
  return gulp.src('./sass/**/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('./css'));
});
```

**Запуск через NPM**

Добавляем в package.json

```json
"scripts": {
    "build": "gulp build"
}
```

build задание по умолчанию, но Вы можете добавить и другие задачи из gulpfile.js

**Отслеживание изменений**

Добавим таск, позволяющий отслеживать изменения

```js
gulp.task('watch', ['sass'], function() {
  gulp.watch('css/**/*.sass', ['sass']);
});
```


**Обфускация**

https://www.npmjs.com/package/gulp-obfuscate


**Полезное чтиво:**

1. Сборка frontend-проекта. Много плагинов
https://habrahabr.ru/post/250569/

2. Еще один пример сборки
https://dmitriyilichev.com/sborka-front-end-proekta-s-pomoshhyu-gulp-i-node-js/

3. Настройка browserSync https://webref.ru/dev/automate-with-gulp/live-reloading

4. Продвинутая сборка проекта на Gulp
https://pugofka.com/blog/technology/the-prepared-starting-package-front-end-development-on-gulp/

5. Подходы к обфускации кода https://habrahabr.ru/post/312172/


**Практика:**
1. Собрать проект с SASS
2. Объединение js-файлов и obfuscator
3. Настроить browser-sync 

