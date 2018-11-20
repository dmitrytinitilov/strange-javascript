#React Старт

Создаем папку проекта big_start и запускаем в ней

```
npm init
```

Это создает package.json нашего проекта

```
npm install --save react react-dom
```

Эта команда заставит npm загрузить модули react и react_dom, а также все нужные им модули, в папку node_modules

Так же в package.json появится раздел dependencies

```json
dependencies: {
    "react":"^15.4.2",
    "react-dom":"^15.4.2"
}
```

Создадим файл .gitignore , для того, чтобы не загружать лишние файлы на Github. Добавим в игнор-список папки

```
node_modules
dist
```

Создадим папку app, в ней файлы index.css и index.js

index.css будет кратким

```
    body {
        background:darkolivegreen;
    }
```

index.js

```js
var React = require('react');
var ReactDOM = require('react-dom');

require('./index.css');

class App extends React.Component {

    render(){
        return (
            <div>
                Hello World!
            </div>
        )
    }
}
```

Поменяем этот код на следующий

```js
var React = require('react');

var ReactDOM = require('react-dom');

require('./index.css');

class App extends React.Component {

    render(){
        return React.createElement (
            "div",
            null,
            "Hello World!"
        );
    }
}
```

Попробуем воспользоваться командой render у ReactDOM

```js
var React = require('react');
var ReactDOM = require('react-dom');

require('./index.css');

class App extends React.Component {

    render(){
        return (
            <div>
                Hello World!
            </div>
        )
    }
}

ReactDOM.render(
    <App />,
    document.getElementById('app')
)

```

Добавим модули к нашему проекту в раздел devDepencies, то есть они будут нужны нам для сборки проекта, но не в самом готовом проекте

```
npm install --save-dev babel-core babel-loader babel-preset-env babel-preset-react css-loader style-loader html-webpack-plugin webpack webpack-dev-server
```

После этого настроим webpack для нашего проекта. Для этого создадим в корне нашего проекта файл webpack.config.js со следующим наполнением

```js
var path = require('path');

module.exports = {
   entry: './app/index.js',
   output: {
       path:path.resolve(__dirname,'dist'),
       filename: 'index_bundle.js'
   }
}
```

Раздел entry говорит Webpack'у, какой файл является ключевым. В разделе output мы задаем директорию, куда будем загружать готовые исходники и имя файла, под которым будет сохраняться результат(наш index_bundle.js)

Добавим модули для обработки наших файлов. Так все файлы с расширением .js будут обрабатываться babel-loader'ом, а .css обработаются style-loader'ом и css-loader'ом.

```js
var path = require('path');

module.exports = {
	entry: './app/index.js',
	output: {
		path: path.resolve(__dirname,'dist'),
		filename: 'index_bundle.js'
	},
	module: {
		rules: [
		{test: /\.(js)$/, use: 'babel-loader'},
		{test: /\.css$/, use: [ 'style-loader', 'css-loader' ]}
		]
	}
}
```

Добавим в наш package.json поднастройки babel

```
"babel": {
    "presets": [
        "env",
        "react"
    ]
}
```

babel-preset-env мы установили ранее, он позволяет динамически добавлять модули необходимые babel для запуска.

babel-react нужен нам для преобразования JSХ

В результате получим package.json следующего вида

```json
{
  "name": "big-start",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "babel": {
    "presets": [
      "env",
      "react"
    ]
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^15.5.4",
    "react-dom": "^15.5.4"
  },
  "devDependencies": {
    "babel-core": "^6.24.1",
    "babel-loader": "^7.0.0",
    "babel-preset-env": "^1.4.0",
    "babel-preset-react": "^6.24.1",
    "css-loader": "^0.28.0",
    "html-webpack-plugin": "^2.28.0",
    "style-loader": "^0.16.1",
    "webpack": "^2.4.1",
    "webpack-dev-server": "^2.4.2"
  }
}

```

Добавим html-webpack-plugin

```js
var path = require('path');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
	entry: './app/index.js',
	output: {
		path: path.resolve(__dirname,'dist'),
		filename: 'index_bundle.js'
	},
	module: {
		rules: [
		{test: /\.(js)$/, use: 'babel-loader'},
		{test: /\.css$/, use: [ 'style-loader', 'css-loader' ]}
		]
	},
	plugins: [new HtmlWebpackPlugin({
		template: 'app/index.html'
	})]
}
```

И создадим в папке app index.html

```html

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Big Start</title>
</head>
<body>
	<div id="app"></div>
</body>
</html>

```
Добавим раздел scripts в наш package.json

```json
"scripts": {
    "create":webpack
}
```

Далее запускаем npm run create

У нас должна создаться папка dist, и в ней два файла index.html и index_bundle.js

index.html имеет следующий вид:

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Github Battle</title>
</head>
<body>
	<div id="app"></div>
<script type="text/javascript" src="index_bundle.js"></script></body>
</html>
```
Мы видим, что внутри кода происходит подключение файла index_bundle.js, который образовался после сборки

Если мы запустим index.html из папки dist, то наконец-то увидим Hello World!

Давайте попробуем автоматизировать обновлени страницы при обновлении кода

```
npm install --save-dev webpack-dev-server
```

Заменим раздел scripts в нашем package.json

```json
"scripts": {
    "start": "webpack-dev-server --open"
}
```

Результирующий package.json будет следующего вида

```json

{
  "name": "big-start",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "webpack-dev-server --open"
  },
  "babel": {
    "presets": [
      "env",
      "react"
    ]
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^15.5.4",
    "react-dom": "^15.5.4"
  },
  "devDependencies": {
    "babel-core": "^6.24.1",
    "babel-loader": "^7.0.0",
    "babel-preset-env": "^1.4.0",
    "babel-preset-react": "^6.24.1",
    "css-loader": "^0.28.0",
    "html-webpack-plugin": "^2.28.0",
    "style-loader": "^0.16.1",
    "webpack": "^2.4.1",
    "webpack-dev-server": "^2.4.2"
  }
}

```

После запуска команды

```
npm run start
```

У нас откроется вкладка с адресом localhost:8080 и при дальнейших изменениях кода, она будет автоматически обновляться

Поздравляю! Вы наконец-то запустили свое первое React-приложение)

**Дополнительные материалы:**

https://maxfarseer.gitbooks.io/react-course-ru