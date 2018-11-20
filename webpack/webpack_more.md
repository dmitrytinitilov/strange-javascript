# Webpack start

**Запуск из командной строки**

```cli
npm install webpack -g
```

Запустим

```cli
webpack src/index.js assets/bundle.js
```

**Создаем build.js**

```js
var path = require('path');
var webpack = require('webpack');
var config = {
    context: path.join(__dirname, 'src'), // исходная директория
    entry: './index', // файл для сборки, если несколько - указываем hash (entry name => filename)
    output: {
        path: path.join(__dirname, 'assets') // выходная директория
    }
};
var compiler = webpack(config);
compiler.run(function (err, stats) {
    console.log(stats.toJson()); // по завершению, выводим всю статистику
});
```

Запуск сборки

```cli
node build
```

**watch:true**

**Webpack dev server**

В том случае, если нам хочется, чтобы после каждых изменений нашего кода происходила автоматическая сборка или же нам просто нужен локальный сервер, лучше настроить webpack dev server.

```cli
npm install webpack-dev-server -g
```

Добавляем в package.json в раздел scripts

```js
"scripts": {
  "start:dev": "webpack-dev-server"
}
```

Запускаем через командную строку

```cli
npm run start:dev
```

В выводе команды обычно указан порт, на котором будет запущен сервер.

Запускаем браузер и смотрим наш сайт

```
localhost:9000
```

_Подробнее:_
https://github.com/webpack/webpack-dev-server



**Глобально вызываемый модуль**

```js
module.exports = {
  output: {
    library: 'myClassName',
  }
};
```

**Загрузка нескольких файлов**

```js
module.exports = {
  entry: ["./global.js", "./app.js"],
  output: {
    filename: "bundle.js"
  }
}
```

**Loader'ы**

**Минификация**

```cli
webpack -p
```

```js
var webpack = require("webpack");

module.exports = {

  entry: "./entry.js",
  devtool: "source-map",
  output: {
    path: "./dist",
    filename: "bundle.min.js"
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin({minimize: true})
  ]
};
```

**Дополнительные материалы:**

Стартовый гайд по Webpack'у  
[https://medium.com/@dabit3/beginner-s-guide-to-webpack-b1f1a3638460\#.vlijhe21f](https://medium.com/@dabit3/beginner-s-guide-to-webpack-b1f1a3638460#.vlijhe21f)

Getting started with Webpack2  
[https://blog.madewithenvy.com/getting-started-with-webpack-2-ed2b86c68783\#.wizy7qh3p](https://blog.madewithenvy.com/getting-started-with-webpack-2-ed2b86c68783#.wizy7qh3p)

[https://survivejs.com/webpack/developing-with-webpack/getting-started/](https://survivejs.com/webpack/developing-with-webpack/getting-started/)

О книге Detailed introduction to webpack, [Joseph Zimmerman](https://www.smashingmagazine.com/author/joseph-zimmerman/)

[www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/](https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/)



7 бед - один ответ  
[https://habrahabr.ru/post/245991/](https://habrahabr.ru/post/245991/)

Скринкаст по Webpack  
[https://www.youtube.com/playlist?list=PLDyvV36pndZHfBThhg4Z0822EEG9VGenn](https://www.youtube.com/playlist?list=PLDyvV36pndZHfBThhg4Z0822EEG9VGenn)

