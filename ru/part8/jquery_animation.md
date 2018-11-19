# # Анимация

**Функции для скрытия/отображения**<BR>
.hide()<BR>
.show()<BR>
.toggle()<BR>

https://www.w3schools.com/jquery/jquery_hide_show.asp

Покажет скрытые элементы за 300 милисекунд

```js
$( '.hidden' ).show( 300 );
```

```js
$( '.hidden' ).show( 'slow' );
```

**Функции сворачивания/разворачивания**<BR>
.slideUp()<BR>
.slideDown()<BR>
.slideToggle()<BR>

http://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_slideup_slidedown

**Функции для появления/исчезновения**<BR>
.fadeOut()<BR>
.fadeIn()<BR>
.fadeToggle()<BR>

https://www.w3schools.com/jquery/jquery_fade.asp

**animate**

http://www.w3schools.com/jquery/eff_animate.asp

Пример<BR>
http://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_animate

```js
$("button").click(function(){
    $("div").animate({left: '250px'});
}); 
```

**Плавный скроллинг к заданной метке**

https://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_animate_smoothscroll


**Вариант вызова №1**

_properties_ - CSS свойства, которые мы анимируем

_duration_ - продолжительность, задается в милисекундах

_easing_ - определяет будут ли ускорения, торможения в анимации(по умолчанию swing, можно поставить linear)

_complete_ - функция, которая вызывает после завершения анимации.

Например:

```js
$( "#clickme" ).click(function() {
  $( "#book" ).animate({
    opacity: 0.25,
    left: "+=50",
    height: "toggle"
  }, 5000, function() {
    // Animation complete.
  });
});
```


```js
$( "#clickme" ).click(function() {
  $( "#book" ).animate({
    width: [ "toggle", "swing" ],
    height: [ "toggle", "swing" ],
    opacity: "toggle"
  }, 5000, "linear", function() {
    $( this ).after( "<div>Animation complete.</div>" );
  });
});
```

**jQuery.fx**

_jQuery.fx.off_ - флаг, который разрешает или запрещает анимации

https://www.w3schools.com/jquery/prop_jquery_fx_off.asp

_jQuery.fx.speeds_ - настройка скорости анимации

```js
// переуставливаем уже определенную скорость
jQuery.fx.speeds.fast = 50;

// создает новую скорость
jQuery.fx.speeds.turtle = 3000;

//Эта анимация проходит за 50 миллисекунд
$( '.hidden' ).hide( 'fast' );

//Можем применить нашу новую скорость
$( '.other-hidden' ).show( 'turtle' );
```

_jQuery.fx.interval_



**Полезное чтиво:**

1. Объяснение базового варианта jQuery.animate
http://papermashup.com/the-jquery-animate-method-explained/

2. Примеры для jQuery.animate
http://viralpatel.net/blogs/understanding-jquery-animate-function/


**Практика:**

1. Сделать блок. При клике на кнопку, если он есть, он исчезает. Если его нет, то он появляется.
2. Сделать сворачивание-разворачивание элементов списка
3. Есть галерея картинок. При клике на картинку, она выезжает на середину экрана и увеличивается.
4. При клике на круг он должен увеличиваться
5. Эффект выезжающих боковинок
https://tympanus.net/Tutorials/LateralOnScrollSliding/
6. Эффекты для типографики
https://tympanus.net/codrops/2011/11/28/typography-effects-with-css3-and-jquery/