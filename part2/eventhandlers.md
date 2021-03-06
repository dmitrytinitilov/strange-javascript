# Способы установки обработчика

http://javascript.ru/tutorial/events/intro

Три способа задания обработчиков событий

**1) Через HTML-атрибут**


```html
<input type="button" value="Нажми здесь" onclick="alert('Работает');" >
```

**2) Через свойство DOM-объекта**

Есть input

```html
<input id="myButton" type="button" value="Нажми меня"/>
```

К нему добавляем обработчик

```js
document.getElementById('myButton').onclick = function() {
    alert('Спасибо')
}
```
либо вот такой вариант

```js

function doSomething() {
    alert('Хватит кликать!');
}

//получаем DOM-объект
input = document.getElementById('myButton');

input.onclick=doSomething;

```


**3) addEventListener**

```html
<input type="submit" id="buttonObj">
```

```js
//код функции обработчика
function doSomething() {
    alert('Хватит кликать!');
}

//получаем DOM-объект
var buttonObj = document.getElementById('buttonObj');

buttonObj.addEventListener( "click" ,doSomething, false); 
// ставим обработчик
```

Обратите внимание, что во втором и третьем случаях мы передаем функцию doSomething, а не ее вызов doSomething(). В третем случае от названия события отбрасывается приставка on

Такой способ позволяет нам устанавливать несколько обработчиков на один и тот же объект.

**removeEventListener**

Функция removeEventListener позволяет убрать обработчик с кнопки

Пример для удаления обработчика событий

```js
var div = document.getElementById('div');
var listener = function (event) {
  /* do something here */
};
div.addEventListener('click', listener, false);
div.removeEventListener('click', listener, false);
```


**Практика:**
1. Есть три DIV'a . При клике на div выводится всплывающее сообщение. На каждом из DIV'ов используется один из способов задания обработчика 
2. Блок. При клике на него он меняет цвет. При повторном клике цвет возвращается
3. Есть два div’a. Если кликнул на первый и на второй – выводится сообщение, что все хорошо
4. Есть массив логинов и форма ввода логина. При вводе логина пользователем, проверяем свободен ли данный логин или нет
5. 	При клике на блок увеличиваем счет
6. 	Есть много кружков. При клике на кружок, его счет увеличивается
7.	Есть большой серый блок и маленькие цветные DIV'ы. При клике на маленький DIV, большой DIV выделяется выбранным цветом .
8.	Выводим круги в случайных позициях со случайными числами внутри. При клике на круг число в нем уменьшается. Когда счет доходит до нуля, круг исчезает — счет увеличивается.
9.  Сделать Cookie Clicker http://orteil.dashnet.org/cookieclicker/ 
10. Сделать интерфейс для ввода логина, пароля



