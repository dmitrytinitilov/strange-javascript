#Webpack Start

Создадим файл home.js

```js
'use strict';

let welcome = require('./welcome');

welcome("home");
```

Создадим файл welcome.js

```js
'use strict';

module.exports = function(message) {
    alert(`Welcome ${message}`);
}
```

Установим webpack

```cli
sudo npm i -g webpack
```

Создадим файл конфигурации webpack.config.js

```js
'use strict';

module.exports = {
    entry: "./home.js",
    output: {
    	filename:"build.js"
    }
}
```

Далее вбиваем в командной строке

```
webpack
```

В результате должны получить build.js, который мы можем добавить к нашему index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<script type="text/javascript" src="build.js"></script>
</head>
<body>
	
</body>
</html>
```

Полученный код может испытывать проблемы в Firefox. Вместо alert'a будем получать ошибку let is a reserved identifier on firefox

Нужно залезть в build.js и поменять let на var

Чуть позже мы воспользуемся для преобразования кода babel'ем
