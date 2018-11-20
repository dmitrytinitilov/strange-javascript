# Angular Старт

Скачиваем angular.js (посмотрите обязательно исходный код этой библиотеки) с https://angularjs.org/ и пробуем запустить данное приложение

```js
<!DOCTYPE html>
<html>
<script src="angular.js"></script>
<body>

<div ng-app="">
  <p>Name: <input type="text" ng-model="name"></p>
  <p ng-bind="name"></p>
</div>

</body>
</html>
```