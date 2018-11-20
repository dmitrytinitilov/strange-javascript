#Scope директив

**scope:false** - директива использует переменные внешнего контроллера. При изменении переменной внутри директивы, мы меняем переменную в контроллере

**scope:true** - директива получает переменные внешнего контроллера, но работает с ними "локально". То есть изменяя значение внутри директивы, мы не меняем значение внутри внешнего контроллера.

**Изолированный scope   scope:{}**

При изолированном scope мы используем атрибут в директиве для связи переменных контроллера и директивы

_@ односторонне связывание, только текст_

В директиву передается значение из атрибута(см пример ниже атрибут connection) 
_
= двустороннее связывание_

Изменения в контроллера передаются в директиву, и наоборот

```js
var app = angular.module('scopeApp', []);

app.controller("AppCtrl", function ($scope) {
  $scope.ctrlName = "Vasya";
})

app.directive("changeName", function () {
  return {
    scope: {
      dirName: "=connection"
    },
    template: '<div>{{ dirName }}</div>',
  };
});
```

```html
<div ng-app="scopeApp">
  <div ng-controller="AppCtrl">
    <input type="text" ng-model="ctrlName"> <!-- Ctrl -->
    <div drink connnection="ctrlName"></div>     <!-- Dir -->
  </div>
</div>
```

_
& использование метода контроллера_


**О различных scope'aх в Angular**


Очень подробно о scope в Angular
http://jonathancreamer.com/working-with-all-the-different-kinds-of-scopes-in-angular/

Fiddle с различными скоупами
https://jsfiddle.net/biondifabio/g3brja67/

http://monsterlessons.com/project/lessons/scope-true-v-diriektivakh-v-angularjs

http://artemdemo.me/blog/scope-%D0%B2-%D0%B4%D0%B8%D1%80%D0%B5%D0%BA%D1%82%D0%B8%D0%B2%D0%B0%D1%85-%D0%B0%D0%BD%D0%B3%D1%83%D0%BB%D0%B0%D1%80%D0%B0-angularjs-directives/

https://www.undefinednull.com/2014/02/11/mastering-the-scope-of-a-directive-in-angularjs/

Об изолированном scope в Angular

http://onehungrymind.com/angularjs-sticky-notes-pt-2-isolated-scope/