# Плагины

Допустим мы хотим добавить свою функцию в возможности jQuery


```js
jQuery.fn.greenbar = function() {
    $(this).css('background','green');
};

$('div').greenbar();
```


**Поддержка цепочек вызова**

//Пример цепочки из двух методов css и html
$("p").css("color","red").html("Новое содержимое");
Для того, чтобы Ваш плагин не "разрывал" цепочку методов необходимо, чтобы он возвращал ключевое слово this.

**Пример**

```js
(function($){
  
   /* Создаем плагин с именем adjust, который будет устанавливать размер текста 
   выбранных элементов равным 1.4em и передавать их дальше по цепочки методов. */
   $.fn.adjust=function(){
   /* Для того, чтобы поддержать цепочку методов нужно вернуть из плагина 
   преобразованную группу выбранных элементов */
      return this.each(function(){
         $(this).css("fontSize","1.4em");
      });
   }

})(jQuery)
```


**Список плагинов**<BR>

50 потрясающих jQuery плагинов<BR>
https://habrahabr.ru/post/175045/

Lightbox для галерей
http://lokeshdhakar.com/projects/lightbox2/

Плагины для скроллинга
http://www.webdesignerdepot.com/2013/12/25-free-scrolling-plugins-for-awesome-experiences/

http://plugins.jquery.com/

http://www.smashingmagazine.com/2011/10/essential-jquery-plugin-patterns/

https://remysharp.com/2010/06/03/signs-of-a-poorly-written-jquery-plugin

https://msdn.microsoft.com/en-us/magazine/ff696759

**jQuery UI**
http://ajpiano.com/widgetfactory/#slide5


http://free.matthieu.com/jquery.parallax-scroll/demo.html


http://www.wisdomweb.ru/JQ/plugin.php

**Примеры**
http://tutorialzine.com/2013/04/50-amazing-jquery-plugins/
Gridster.js
jQuery Countdown

**Полезное чтиво:**

1. Пишем плагин на jQuery
https://habrahabr.ru/post/158235/


**Практика:**

1. Сделать плагин, который бы раскрашивал блоки в зависимости от их размера
2. Сделать плагин, который оборачивает все красные элементы в границу толщиной 10 пикселей. Добиться возможности цепочечных вызовов