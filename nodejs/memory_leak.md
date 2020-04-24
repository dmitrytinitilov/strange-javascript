#Утечки памяти


```cli
npm install heapdump --save
```

Если получаем ошибку

Can't find Python executable "python"

Запускаем

```cli
npm install --global --production windows-build-tools
```

Подключаем наш модуль

```js
var heapdump = require('heapdump');
```


Для того, чтобы сделать снимок пишем код

```js
heapdump.writeSnapshot(function(err, filename) {
  console.log('dump written to', filename);
});
```

Зоходим в Chrome -> Memory или Profile и загружаем снимок

**Полезное чтиво:**

1. https://www.alexkras.com/simple-guide-to-finding-a-javascript-memory-leak-in-node-js/

2. https://habr.com/ru/company/plarium/blog/277129/?_ga=2.249198855.1093392857.1557918184-889482411.1553785346

3. https://medium.com/tech-tajawal/memory-leaks-in-nodejs-quick-overview-988c23b24dba