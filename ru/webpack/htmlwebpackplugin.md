#HtmlWebpackPlugin

HtmlWebpackPlugin занимается тем, что генерирует для html-файл по шаблону при сборке

Для использования плагина нам необходимо добавить его в dev-зависимости

```
npm install --save-dev html-webpack-plugin
```

После чего наш webpack.config.js нужно изменить на следующий код 

```js
'use strict';

var path = require('path');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
	entry:'./app/home.js',
	output: {
		path:path.resolve(__dirname,'dist'),
		filename: 'bundle.js'
	},
	plugins: [new HtmlWebpackPlugin({
		template: 'app/index.html'
	})]

}
```

То есть мы добавляем сверху подключение модуля нашего плагина
```js
var HtmlWebpackPlugin = require('html-webpack-plugin');
```

и добавляем его в настройки

```js
plugins: [new HtmlWebpackPlugin({
		template: 'app/index.html'
	})]
```

В качестве шаблона используем наш index.html, который мы перенесли в папку app




