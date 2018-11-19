#ESLint

**Базовая установка**

https://packagecontrol.io/packages/ESLint

Предполагается, что у нас на компьютере уже установлен nodejs и npm

1. Устанавливаем eslint через npm в наш проект

```
npm install eslint
```

Или глобально, если хотим, чтобы оно сработало для всех проектов

```
npm install -g eslint
```

2. Настраиваем или скачиваем .eslintrc

```json
{
  "globals": {
    // Put things like jQuery, etc
    "jQuery": true,
    "$": true
  },
  "env": {
    // I write for browser
    "browser": true,
    // in CommonJS
    "node": true
  },
  // To give you an idea how to override rule options:
  "rules": {
    // Tons of rules you can use, for example...
    "quotes": [1, "double"]
  }
}
```

3. В Sublime устанавливаем через Package Control, пакет ESLint

Далее по клику правой клавишей в открывшемся меню выбираем ESLint, либо нажимаем Ctrl+Alt+e

F4 - перейти на следующую ошибку
Shift + F4 - вернуться на предыдущую ошибку

**Настраиваем правила**

0 - Отключить правило
1 - Warn - правило предупреждение
2 - Error - правило бросает ошибку

Полный список правил можно найти вот здесь
http://eslint.org/docs/rules/

**Настраиваем ESLint под настройки Airbnb**

```
npm install --save-dev eslint-config-airbnb
```

в .eslintrc добавляем

```
"extends": "airbnb"
```

**Дополнительное чтиво:**

1. Установка ESLint на Sublime Text
http://jonathancreamer.com/setup-eslint-with-es6-in-sublime-text/

2. Настраиваем ESLint под настройки Airbnb
https://medium.freecodecamp.org/adding-some-air-to-the-airbnb-style-guide-3df40e31c57a

3. Настройка Linter'ов на Sublime
https://habrahabr.ru/post/278747/