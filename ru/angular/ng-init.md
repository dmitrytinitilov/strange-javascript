# ng-init

Директива ng-init позволяет устанвливать начальные значения переменным. Например:

```js
ng-init="firstName='John'"
```

```html
<div ng-app="" ng-init="quantity=1;cost=5">
<p>Total in dollar: {{ quantity * cost }}</p>
</div>
```
Директива ng-bind позволяет "привязать" переменную к html-коду

```html
<div ng-app="" ng-init="quantity=1;cost=5">
	<p>Total in dollar: <span ng-bind="quantity * cost"></span>	</p>
</div>
```
Значение переменной может быть объектом

```html
<div ng-app="" ng-init="person=	{firstName:'John',lastName:'Doe'}">
	<p>The name is {{ person.lastName }}</p>
</div>
```

**Практика:**

1) Вывести прямоугольник по вводимым координатам

