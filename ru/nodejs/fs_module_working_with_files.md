# Модуль fs. Работа с файлами

https://github.com/visionmedia/masteringnode/blob/master/chapters/fs.md
<BR>
http://ru.code-maven.com/list-content-of-directory-with-nodejs

Считываем данные с директории

```js
fs.readdir(path, function(err, items) {
    for (var i=0; i<items.length; i++) {
        var file = path + '/' + items[i];
 
        console.log("Start: " + file);
        fs.stat(file, generate_callback(file));
    }
});
 
function generate_callback(file) {
    return function(err, stats) {
            console.log(file);
            console.log(stats["size"]);
        }
};
```

**Считывание файла по строкам:**
http://stackoverflow.com/questions/6156501/read-a-file-one-line-at-a-time-in-node-js

```js
var lineReader = require('readline').createInterface({
  input: require('fs').createReadStream('file.in')
});

lineReader.on('line', function (line) {
  console.log('Line from file:', line);
});
```

**Считывание удаленного файла**

Воспользуемся модулем request

```
npm i request
```

```js
var request = require('request');
request.get('http://www.whatever.com/my.csv', function (error, response, body) {
    if (!error && response.statusCode == 200) {
        var csv = body;
        // Continue with your processing here.
    }
});
```


https://stackoverflow.com/questions/14552638/read-remote-file-with-node-js-http-get


**Получение подробной информации о файле**
http://ru.code-maven.com/system-information-about-a-file-or-directory-in-nodejs

**Практика:**

1. Считать из файла два числа. Найти их сумму
2. В файле в первой строчке заданы размеры карты m n. Далее, в последующих m строках указаны n символов, кодирующие ячейки карты. * - обычная ячейка, # - сундук. Требуется найти координаты сундука.
3. Считать данные с удаленного сайта и записать их в файл (например, файл погоды)
