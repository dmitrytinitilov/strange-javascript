#CSS в Webpack'e

Нам понадобятся style-loader, css-loader

настройки подключения

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [ 'style-loader', 'css-loader' ]
      }
    ]
  }
}
```

в файл, который является точкой входа добавляем import('./styles.css');

```js
'use strict';

require('./styles.css');
let welcome = require('./welcome');

welcome("home");
```

и в результате получаем вот так вот webpack.config.js

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
	module: {
    rules: [
      {test: /\.css$/,  use: [ 'style-loader', 'css-loader' ]}
    ]
  	},
	plugins: [new HtmlWebpackPlugin({
		template: 'app/index.html'
	})]

}
```


**Полезное чтиво:**

1. Разбираемся с CSS
https://monsterlessons.com/project/lessons/sborshchik-moduliei-webpack-razbiraiemsia-s-css-chast-3

2. Получаем внешний css-файл с помощью webpack
https://webpack.js.org/plugins/extract-text-webpack-plugin/#usage-example-with-css

3. Работа с CSS
https://webpack.github.io/docs/stylesheets.html