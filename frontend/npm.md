#NPM

Рассмотрим работу с NPM для фронтенд-разботки

**npm init**

инициализирует рабочее пространство проекта. Добавляется файл package.json с характеристиками проекта.

```cmd
npm init
```

**package.json**

```json
{
  "name": "bingo",
  "version": "0.0.1",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "dmitry tinitilov",
  "license": "MIT"
}
```

**Работа со scripts**

У нас есть раздел scripts, в котором есть команда test. Команда npm test запустит код, указанный в package.json

```cmd
npm test
```

**npm install jquery**

```cmd
npm install jquery
```

**добавление в зависимости**

```cmd
npm install jquery --save
```

```json
{
  "name": "bingo",
  "version": "0.0.1",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "dmitry tinitilov",
  "license": "MIT",
  "dependencies": {
    "jquery": "^3.2.1"
  }
}
```


**Полезное чтиво:**

1. Продвинутая настройка NPM
https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/



