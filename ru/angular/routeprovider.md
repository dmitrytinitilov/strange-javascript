# $routeProvider, $locationProvider

**Базовый роутинг**
https://www.w3schools.com/angular/angular_routing.asp

Построение одностраничного приложения на Angular
https://scotch.io/tutorials/single-page-apps-with-angularjs-routing-and-templating

Убираем хештег из адресов
https://scotch.io/tutorials/pretty-urls-in-angularjs-removing-the-hashtag

**Динамический роутинг**

http://stackoverflow.com/questions/20637999/angularjs-use-routeprovider-when-variables-to-construct-templateurl-name

```js
.when('/pages/:pageName', {
    templateUrl: function(params) {
        return 'views/pages/' + params.pageName + '.html';
    },
    controller: 'MainController'
});
```

**Примеры:**

Список студентов
http://www.journaldev.com/6225/angularjs-routing-example-ngroute-routeprovider
