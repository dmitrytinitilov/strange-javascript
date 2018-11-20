# Контроллеры

http://www.w3schools.com/angular/angular_controllers.asp

Пример простого контроллера

```html
<div ng-app="myApp" ng-controller="myCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstName = "John";
    $scope.lastName = "Doe";
});
</script>
```

Еще один пример

```html
<div ng-app="" ng-controller="myCtrl">

<button ng-click="count = count + 1">Click me!</button>

<p>{{ count }}</p>

</div>
```

```html
<body ng-controller="MainCtrl">
    <p>Hello {{name}}!</p>
    {{msg}}
    <a ng-href='#here' ng-click='go()' >click me</a>
    <div style='height:1000px'>

      <a id='here'></a>

    </div>
     <h1>here</h1>
  </body>

var app = angular.module('plunker', []);

app.controller('MainCtrl', function($scope) {
  $scope.name = 'World';

  $scope.go = function() {

    $scope.msg = 'clicked';
  }
});
```


ng-click вместе ng-hide
```html
<div ng-app="myApp" ng-controller="personCtrl">

<button ng-click="toggle()">Toggle</button>

<p ng-hide="myVar">
First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}
</p>

</div>

<script>
var app = angular.module('myApp', []);
app.controller('personCtrl', function($scope) {
    $scope.firstName = "John",
    $scope.lastName = "Doe"
    $scope.myVar = false;
    $scope.toggle = function() {
        $scope.myVar = !$scope.myVar;
    };
});
</script>
```

**Примеры:**

5-ть практических примеров использования Angular

http://tutorialzine.com/2013/08/learn-angularjs-5-examples/


**Практика:**

1. Сделать кликер
2. Сделать блок-мигалку (при клике переключает цвет с первого на второй, со второго на первый)
3. Сделать проверку данных из формы для ввода логина-пароля
4. Сделать приложение - список покупок
