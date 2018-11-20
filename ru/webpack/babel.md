#Babel

```
npm install --save-dev babel-loader babel-core babel-preset-env
```

В наш webpack.config.js нужно будет добавить строчку с правилом на сборку babel-loader'a

```js
module: {
  rules: [
    {
      test: /\.js$/,
      exclude: /(node_modules|bower_components)/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['env']
        }
      }
    }
  ]
}
```

Если всё настроено правильно, то после сборки наши файлы

home.js

```js
'use strict';

let welcome = require('./welcome');

welcome("home");
```

и welcome.js

```js
'use strict';

module.exports = function(message) {
    alert(`Welcome ${message}`);
}
```

должны выдать фразу Welcome home


**Подробнее:**
https://github.com/babel/babel-loader