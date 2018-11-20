#Разделение исходников и результата

Перенесем наши исходники в папку app и добъемся, чтобы файлы сборки помещались в папку dist. index.html останется на своем старом месте

Нам придется изменить webpack.config.js

```js
module.exports = {
	entry:'./app/home.js',
	output: {
		path:path.resolve(__dirname,'dist'),
		filename: 'bundle.js'
	}

}
```
и изменить путь и название подключаемого файла в index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script type="text/javascript" src="dist/bundle.js"></script>
</head>
<body>

</body>
</html>

```


