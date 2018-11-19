# Сервисы

http://www.w3schools.com/angular/angular_services.asp

Список встроенных сервисов Angular
http://www.techstrikers.com/AngularJS/angularjs-built-in-services.php

**$http сервис**

```js
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http.get("welcome.htm").then(function (response) {
      $scope.myWelcome = response.data;
  });
});
```

```html
<!DOCTYPE html>
<html>
<script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl"> 

<p>Today's welcome message is:</p>

<h1>{{myWelcome}}</h1>

</div>

<p>The $http service requests a page on the server, and the response is set as the value of the "myWelcome" variable.</p>


</body>
</html>
```

Еще один пример с $http-сервисом

```html
<div ng-app="myApp" ng-controller="customersCtrl">

<ul>
<li ng-repeat="x in names">
{{ x.Name + ', ' + x.Country }}
</li>
</ul>

</div>

<script>
var app = angular.module('myApp', []);
app.controller('customersCtrl', function($scope, $http) {
$http.get("http://www.w3schools.com/angular/customers.php")
.success(function(response) {$scope.names = response.records;});
});
</script>
```


**Создание своего собственного сервиса**

```js
app.service('hexafy', function() {
    this.myFunc = function (x) {
        return x.toString(16);
    }
});
```
Вызов своего собственного сервиса

```js
app.controller('myCtrl', function($scope, hexafy) {
    $scope.hex = hexafy.myFunc(255);
});
```

**Практика:**

1. Делаем трехстраничный сайт, используя $http
2. Сделать подгрузку товаров при прокрутке в интернет магазине