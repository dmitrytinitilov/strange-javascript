# POST-параметры

Когда мы создаем сервер у нас создаются два потока, так называемые Stream. Request или req является Readable Stream. Когда нам приходит часть данных, у Readable Stream срабатывает событие _data_. Когда все части данных присланы происходит событие _end_

```js
var http = require('http');
var fs   = require('fs');
var qs = require('querystring');
 
http.createServer(function (req, res) {
    if (req.method == 'POST') {
       var body = '';

        req.on('data', function (data) {
            body += data;
        });

        req.on('end', function () {
        	var obj = qs.parse(body)
            console.log(obj.test);
        });
    } else {
    	fs.readFile('form.html', function (err, data){
	        if (err) {
	            res.end("File wasn't found");
	        }
	        res.writeHeader(200, {"Content-Type": "text/html"});  
	        res.end(data);
	    });
    }
}
).listen(8080);
```

файл form.html

```html
<form action="/" method="POST">
	<input type="text" name="test">
	<input type="submit" value="Отправить">
</form>
```

Иногда нам нужно избавиться от POST-параметров, чтобы при обновлении страницы пользователю не выводилось сообщение.

```js
response.writeHead(302, {
  'Location': 'your/404/path.html'
  //add other headers here...
});
response.end();
```

**Перенаправление на стороне сервера**

Чтобы избавиться от POST-параметров делаем перенаправление на стороне сервера

```js
res.writeHead(302, {'Location': '/ok'});
res.end();

```

**Установка кодировки**

```js
res.writeHeader(200, {"Content-Type": "text/html"});  
```



**Построение echo-сервера на NodeJS**

https://debugmode.net/2014/01/14/create-echo-server-in-node-js/

**Дополнительные материалы:**  

Как извлечь POST-данные в NodeJS
http://stackoverflow.com/questions/4295782/how-do-you-extract-post-data-in-node-js

[https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/](https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/)

[http://ru.code-maven.com/http-client-request-in-nodejs](http://ru.code-maven.com/http-client-request-in-nodejs)

Запрос к удаленному серверу  
[https://docs.nodejitsu.com/articles/HTTP/clients/how-to-create-a-HTTP-request/](https://docs.nodejitsu.com/articles/HTTP/clients/how-to-create-a-HTTP-request/)

**Практика:**

1. Есть форма для ввода логина, пароля. Если и логин и пароль совпали - вывести пользователю поздравление. Если нет, выводим сообщение о просьбе ввести данные повторно и форму для ввода.

2. Пользователь вводит число в форму. В ответ ему опять выводится форма. Так происходит до тех пор, пока пользователь не введет 0. После этого выводим сумму всех введенных чисел.
