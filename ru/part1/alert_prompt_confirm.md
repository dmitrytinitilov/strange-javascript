# alert prompt confirm

prompt открывает окно на запрос данных у пользоваля.

```js
var s = prompt('Введите Ваше имя');

alert('Добрый день, '+s);
```

prompt всегда возвращает строку. Чтобы преобразовать ее к числу у нас есть два варианта

```js
var a = parseInt(prompt('Введите число'));
```

или более короткий

```js
var a = +prompt('Введите число'));
```


**Практика:**

1. Запрашиваем у пользователя два числа и выводим их сумму

2. Запрашиваем у пользователя числа, до тех пор пока не введет 0. Выводим сумму всех раннее введенных чисел

3. Запрашиваем у пользователя числа, до тех пор пока не введет 0. Выводим максимальное из всех раннее введенных чисел.

4. Запрашиваем у пользователя числа, до тех пор пока не введет 0. Из всех раннее введенных чисел выводим второе по величине число после максимального.
5.	Задача угадай число (загадываем число, пользователь пытается угадать, вводя числа. Мы возвращаем больше или меньше)
6.	Камень ножницы бумага (вариант вводится как буква, а компьютер выбирает свой через rand)