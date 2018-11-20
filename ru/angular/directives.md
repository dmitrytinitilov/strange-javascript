# Директивы

Директива расширяет HTML с помощью атрибутов и элементов

Создание собственной директивы

```html
<body ng-app="myApp">

<w3-test-directive></w3-test-directive>

<script>
var app = angular.module("myApp", []);
app.directive("w3TestDirective", function() {
    return {
        template : "<h1>Made by a directive!</h1>"
    };
});
</script>

</body>
```

Данная директива выведет на месте &lt; w3-test-directive&gt; &lt; /w3-test-directive&gt; код &lt; h1&gt; Made by a directive!&lt; /h1&gt;

Подробнее о вариантах http://www.w3schools.com/angular/angular_directives.asp



**закрытые элементы**

```html
<div ng-app="">

<p>
<button ng-disabled="mySwitch">Click Me!</button>
</p>

<p>
<input type="checkbox" ng-model="mySwitch">Button
</p>

</div>
```

**Полезное чтиво:**

Директивы в Angularjs для начинающих. Часть 1

https://habrahabr.ru/post/179755/

Директивы в Angularjs для начинающих. Часть 2

https://habrahabr.ru/post/180365/

Разбор структуры директив по кусочкам

https://habrahabr.ru/post/164493/

Хранилище примеров от Андреева Артема

https://github.com/andreev-artem/angular_experiments

**Практика:**

1. Сделать DIV с параметром value, который превращается в progress bar


