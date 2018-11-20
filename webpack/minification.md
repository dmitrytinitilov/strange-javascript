#Минификация

Для минификации нам понадобится плагин webpack.optimize.UglifyJsPlugin

Конфигурация для минификации
```js
var webpack = require("webpack");
var path = require('path');

module.exports = {

  entry: "./home.js",
  devtool: "source-map",
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: "bundle.min.js"
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin({minimize: true})
  ]
};
```

Вызов минификации из командной строки
```
webpack -p
```