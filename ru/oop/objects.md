# Способы создания объекта в JavaScript

4-ре способа создать объект в JavaScript  
[https://habrahabr.ru/post/17613/](https://habrahabr.ru/post/17613/)

**1-й способ new Object\(\)**

Object - стандартный конструктор JavaScript

```js
var person = new Object();
//создадим свойство
person.name = 'Petya';

person.getName = function() {
  return this.name;
  //this содержит ссылку на объект
}
```

**2-й способ Литеральная нотация**

```js
var person = {
  name:'Petya',
  getName:function() {
    return this.name;
  }
}
```

Мы можем объединить два способа в один

```js
var person ={}; //вместо new Object

person.name = 'Petya';

person.getName = function() {
  return this.name;
}
```

**3-й способ работаем с объектом как с ассоциативным массивом**

```js
var person = new Object();

person["name"] = 'Petya';

person["getName"] = function() {
  return this.name;
}
```

Кстати, это единственный способ работать со свойствами, содержащими пробел в названии.

**4-й способ создание объекта через конструктор**

```js
function CreatePerson(name) {
  this.name = name; //сохраняем параметр в свойстве объекта
  this.getName = function() {
    return this.name;
  }
}

//от одного конструктора можно генерировать сколько угодно объектов
var person = new CreatePerson('Petya'); 
var person2 = new CreatePerson('Vasya');
```

Чтобы сгенерировать объект, конструктор вызывается через new

Обычно такой способ создания объектов вызывает трудности в понимании у начинающих. По сути происходит следующее. Когда мы вызываем функцию конструктор через new, создается пустой объект {}, внутрь него мы помещаем функцию конструктор и вызываем ее. То есть процесс выглядит вот так:

```js
var person = {}

person.CreatePerson = function(name) {
   this.name = name; //сохраняем параметр в свойстве объекта
   this.getName = function() {
      return this.name;
   }
}

person.CreatePerson('Petya');
```

Как видите name передается в свойство this.name нового объекта. Функция сохраняется в свойство getName объекта.

Часто конструктор по ошибке вызывают без new. В этом случае он просто добавляет глобальные переменные.

```js
var name = 'Vasya';

function CreatePerson(name) {
    this.name = name; 
    this.getName = function() {
        return this.name;
    }
}

var obj = CreatePerson('Petya');

console.log(obj);//Undefined, потому что CreatePerson ничего не возвращает

console.log(name);//вернет Petya, потому что вызов конструктора изменил значение name

console.log(getName);//вернет код функции getName
```

**Добиваемся, чтобы конструктор вызывался без new**

```js
function User(name, passwordHash) {
    if (!(this instanceof User)) {
        return new User(name, passwordHash);
    }
    this.name = name;
    this.passwordHash = passwordHash;
}
```

То есть, если у нас функцию User запустили через new, this будет указывать на новый объект. Если же User была вызвана как обычная функция, то мы генерируем вызов с new сами.

**Методы и свойства**

Традиционно, в ООП свойством называется переменная внутри объекта, а методом функция вызываемая из объекта. В JavaScript'е граница несколько размыта, потому что методом по сути является свойство, в котором хранится функция. Давайте посмотрим пример. Сделаем объект для "приветствия". То есть у нас есть два свойства приветсвие и имя адресата, а также метод, который это приветствие возвращает.

```js
var GreetingObj = {

    greeting:'Hello',
    name:'Petya',
    makeGreeting: function() {
        return this.greeting+' '+this.name
    }  
}

//Вызовем метод makeGreeting
var result = GreetingObj.makeGreeting();

console.log(result);
```

То есть greeting и name являются свойствами, а makeGreeting методом. Вызвать метод можно через объект GreetingObj.makeGreeting\(\)

**Хранение объектов**

```js
var obj = {}

obj.a = 5;

var obj2 = obj;

obj2.a = 7;

console.log(obj.a);//?
```

**Дополнительные материалы:**

Разбирается много странных ситуаций, что может хорошо продвинуть понимание. Без базового понимания, сюда лучше не лезть  
[https://habrahabr.ru/post/119391/](https://habrahabr.ru/post/119391/)

Много всего, но на этом этапе будет сложно  
[https://habrahabr.ru/post/48542/](https://habrahabr.ru/post/48542/)

Выразительный JavaScript::Тайная жизнь объектов  
[https://habrahabr.ru/post/241587/](https://habrahabr.ru/post/241587/)

**Практика:**

1. Сделать объект с двумя свойствами и одним методом, который выводит их сумму.
2. Сделать объект \(через конструктор\), который хранит ширину, высоту и фоновый цвет прямоугольника
3. Создаем отдельную функцию, в которую передается объект. Функция рисует его в два раза больше.
4. Конструктор Car \(передаем скорость\) + метод Go. Добавляем машину, которая телепортируется
5. Создаем функцию, в которую передаем два объекта от Car. Определяем, кто победил.  Смотреть, чтобы не было много return
6. Объект со свойством и методом show, которое выводит этот x через alert
7. Реализовать BlackJack с другим игроком
8. Создать объект галерею, внутри которого есть массив с адресами фотографий, а также три метода: printGallery - выводит галерею на экран, printImage\(i\) - выводит i-ю фотографию из массива, getNumberOfPhotos\(\) - возвращает количество фотографий в галерее.



