# #COFFEE AJAX

```js
$("button").click(function(){
    $.ajax({url: "demo_test.txt", success: function(result){
         $("#div1").html(result);
    }});
});
```

```js
$.ajax({
  url: url,
  type: "POST",
  data: data,
  success: success,
  dataType: dataType
});
```


```js
$.ajax({
    url: '/ajax/example.html',             // указываем URL и
    dataType : "json",                     // тип загружаемых данных
    success: function (data, textStatus) { // вешаем свой обработчик на функцию success
        $.each(data, function(i, val) {    // обрабатываем полученные данные
            /* ... */
        });
    } 
});

```

**Полезное чтиво:**

1. Загрузка картинки на сервер с помощью ajax  
  https://stackoverflow.com/questions/19447435/ajax-upload-image
  

**Практика:**

1. Передаем на сервер два числа - получаем сумму двух чисел

2. Получить с сервера список имен и телефонов пользователей в виде JSON-файла.
  
