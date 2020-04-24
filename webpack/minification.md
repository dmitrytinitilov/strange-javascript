#Минификация

Для минификации нам понадобится плагин UglifyJs

```cmd
npm install uglifyjs-webpack-plugin --save-dev
```


Конфигурация для минификации
```js
'use strict';

var path = require('path');
var HtmlWebpackPlugin = require('html-webpack-plugin');

const UglifyJsPlugin = require('uglifyjs-webpack-plugin');

module.exports = {
    entry:'./app/home.js',
    output: {
        path:path.resolve(__dirname,'dist'),
        filename: 'bundle.js'
    },
    plugins: [new HtmlWebpackPlugin({
        template: 'app/index.html'
    })],
    optimization: {
    	minimizer: [new UglifyJsPlugin()],
  	}

}
```
