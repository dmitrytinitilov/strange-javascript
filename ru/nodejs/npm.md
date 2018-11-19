#NPM

**Инициация package.json**

package.json - файл, который хранит в себе всю необходимую информацию о Вашем модуле

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

Для того, чтобы сгенерировать package.json с помощью npm необходимо запустить
```
npm init
```

При этом нужно будет ответить на вопросы npm, либо нажать несколько раз Enter   

Автоматическая генерация package.json выполняется с помощью
```
npm init --yes
```

**Добавление зависимостей**

Если для нашего модуля нужен jQuery, с добавлением в зависимости, то используем команду

```
npm install jquery --save
```
После чего в наш package.json добавиться свойство _dependencies_

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

Для сборки проекта нам также нужны модули. Для их установки используем команду install с ключем --save-dev

```
npm install --save-dev babel-core
```

**Запуск настраиваемых скриптов**

В свойстве scripts package.json можно добавлять свои команды, например

```json
"scripts": {
  "build": "webpack"
},
```

Предварительно нужно проинсталлировать webpack
```
npm install webpack
```

После его настройки можно будет запустить команду

```
npm run build
```


**Публикация модуля**

Регистрация или залогинивание
```
npm adduser
```

Публикация модуля из текущей директории
```
npm publish
```

Поиск модуля
```
npm search your_module
```

Установка модуля
```
npm install your_module
```

Удаление модуля из текущей папки
```
npm remove your_module
```

Удаление модуля из репозитория NPM
```
npm unpublish
```


Введение в NPM

[https://www.youtube.com/watch?v=fhwtUW9dXrA&list=PLDyvV36pndZFWfEQpNixIHVvp191Hb3Gg&index=7](https://www.youtube.com/watch?v=fhwtUW9dXrA&list=PLDyvV36pndZFWfEQpNixIHVvp191Hb3Gg&index=7)

Структура пакета NPM

[https://www.youtube.com/watch?v=CrevZgTc7ow&list=PLDyvV36pndZFWfEQpNixIHVvp191Hb3Gg&index=8](https://www.youtube.com/watch?v=CrevZgTc7ow&list=PLDyvV36pndZFWfEQpNixIHVvp191Hb3Gg&index=8)



Создание собственного NPM-модуля

[https://medium.com/@jdaudier/how-to-create-and-publish-your-first-node-js-module-444e7585b738\\#.49e5dlo31](https://medium.com/@jdaudier/how-to-create-and-publish-your-first-node-js-module-444e7585b738\#.49e5dlo31)

```cli
npm init
```

[https://docs.npmjs.com/cli/init](https://docs.npmjs.com/cli/init)

О package.json

[http://browsenpm.org/package.json](http://browsenpm.org/package.json)

[https://docs.npmjs.com/getting-started/using-a-package.json](https://docs.npmjs.com/getting-started/using-a-package.json)

NPM для новичков

[https://habrahabr.ru/post/243335/](https://habrahabr.ru/post/243335/)

Подготовка собственного пакета

[https://habrahabr.ru/post/206678/](https://habrahabr.ru/post/206678/)

Более тонкая настройка NPM
http://prgssr.ru/development/vvedenie-v-paketnyj-menedzher-npm-dlya-nachinayushih.html

**Практика:**

1. Сделать модуль, который по массиву чисел возвращает гистограмму

