# Использование this в обработчиках

```js
function func() {
      this.style.backgroundColor = 'red';
}

var obj1 = document.getElementById('obj1');
var obj2 = document.getElementById('obj2');

obj1.onclick = func;
obj2.onclick = func;
```

**Практика:**

1. Есть кружки с числами. При клике на кружок, число внутри должно уменьшиться на единицу. Использовать один обработчик для всех кружков.

2. Сгенерировать блоки. Установить на них всех(в цикле) один обработчик, который при клике на блок меняет его цвет.

3. Сделать предыдущее задание, чтобы активным был только один блок.  

4. Есть четыре блока. При клике на один из них, блок становится «активным»(меняет цвет), остальные «деактивируются»

5. Есть меню с вложенными подпунктами. Сделать, чтобы при клике на пункт разворачивались его подпункты

6. Наперстки. Компьютер прячет от нас бонус за одним из блоков. Наша задача угадать, под каким.

7. Маджонг. Есть карты, перевернутые рубашками вверх. Если мы кликаем на карту, она на время переворачивается. Если мы успеваем кликнуть на вторую карту и она оказывается такой же, то они обе одновременно переворачиваются.