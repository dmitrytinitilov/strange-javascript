#Обфускация

Иногда нам нужно сделать наш код заведомо непонятным для внешних программистов. Для этого используется такая вещь как обфускатор

Для этого установим плагин webpack-obfuscator

```cmd
npm install --save-dev webpack-obfuscator
```

Настроим webpack.config.js

```js
var HtmlWebpackPlugin = require('html-webpack-plugin');

const UglifyJsPlugin = require('uglifyjs-webpack-plugin');
var JavaScriptObfuscator = require('webpack-obfuscator');

module.exports = {
	mode: 'development',
    entry:'./app/home.js',
    output: {
        path:path.resolve(__dirname,'dist'),
        filename: 'bundle.js'
    },
    plugins: [new HtmlWebpackPlugin({
        template: 'app/index.html'
    }), new JavaScriptObfuscator ({
      rotateUnicodeArray: true
  })],
    optimization: {
    	minimizer: [new UglifyJsPlugin()],
  	}

}

```