# ng-repeat

Директива ng-repeat позволяет проходиться по элементам массива в переменной

```js
<div ng-app="" ng-init="names=['Jani','Hege','Kai']">
  <ul>
    <li ng-repeat="x in names">
      {{ x }}
    </li>
  </ul>
</div>
```

В случае прохода по элементам объекта как по ассоциативному массиву, синтаксис становится следующим:

```html
<div ng-repeat="(key, value) in myObj"> ... </div>
```

```html
<tr ng-repeat="(key, value) in data">
    <td>{{key}}<input type="text" ng-model="data[key]"></td>
</tr>
```

Пример для случая многомерных массивов

```html
<ul>
    <li ng-repeat="category in categories">
        {{ category.title }}
        <ul ng-if="category.categories">
            <li ng-repeat="category in category.categories">
                {{ category.title }}
            </li>
        </ul>
    </li>
</ul>
```



**Практика:**

1. Вывести несколько div'ов в цикле
