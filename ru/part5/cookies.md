# cookies

Запускать под сервером. Локально работает только под Mozilla


Записывает куку userName со значением Vasya

```js
document.cookie = "userName=Vasya";
```

Записывает куку cn со значением 2 и fn со значением 3

```js
document.cookie='cn=2';

document.cookie='fn=3';
```

Чтобы переписать куку нужно ее повторно переустановить

```js
document.cookie='cn=1';

document.cookie='cn=2';
```
То есть кука cn станет равной двум

Полный формат записи кук
```
<name>=<value>[;expires=<date>][;path=<some_path>][;domain=<domain_name>][;secure]
```

Пример с использованием свойства path

```js
<script type="text/javascript">
    document.cookie = "name1=11; path=/;";
    document.cookie = "name2=13; path=/;";
    alert(document.cookie);
</script>
```
**Установка куки на час**

```js
var now = new Date();
var time = now.getTime();
time += 3600 * 1000;
now.setTime(time);
document.cookie = 
'username=' + value + 
'; expires=' + now.toUTCString() + 
'; path=/';
```

**Считывание значения cookie**

```js
	function read_cookie(key)
	{
	    var result;
	    return (result = new RegExp('(?:^|; )' + encodeURIComponent(key) + '=([^;]*)').exec(document.cookie)) ? (result[1]) : null;
	}
```

Либо использование библиотеки jQuery

https://github.com/carhartl/jquery-cookie

	
using jquery-cookie

I find this library helpful. 3.128 kb of pure convenience.

add script

```js
<script src="/path/to/jquery.cookie.js"></script>

//установка значения
$.cookie('name', 'value');

//считывание значения
$.cookie('name');
```

**Практика:**

1.	Сделать выбор цвета у прямоугольника и его сохранение
2.	Делаем страницу, которая считает количество своих загрузок
3.	Делаем проверку логина пароля. Если пользователь ввел правильно, выводим кубок
4.	Делаем два блока с выбором цвета. После перезагрузки страницы цвета блока сохраняются.
5. Пишем Томагочи

