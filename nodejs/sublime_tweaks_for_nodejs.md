# Настройка Sublime для NodeJS

**Настройка Build System**

Выбираем:
Tools > Build System > New Build System

Для Ubuntu

```json
{
  "cmd": ["/usr/local/bin/node", "$file"],
}
```

Для Windows

```json
{
  "cmd": ["C:/Program Files/nodejs/node.exe", "$file"],
  "selector": "source.js"
}
```

Подробная статья
https://pawelgrzybek.com/javascript-console-in-sublime-text/


Для открытия в командной строке в Windows

```json
{
  "cmd": ["node", "$file"],
  "selector": "source.js",
  "windows" : {
     "shell": true
  }
}
```

Подробнее тема
http://stackoverflow.com/questions/20844421/sublime-text-3-build-system-node-js-npm-module-not-executing

**Перезапуск сервера при обновлении кода**

```cli
npm install -g nodemon
```

Для проверки того, что nodemon установился вбиваем в командную строку

```cli
nodemon -h
```

Если не находит команду, то скорее всего проблема с путями npm

Заходим в Tools\Build System\New build system

Меняем build system на

```json
{
  "cmd": ["nodemon", "$file"],
  "windows" : {
     "shell": true
  }
}
```
Для запуска Build System нажимаем Ctrl+Shift+B


**Управление процессами**

Если получаем
```cli
events.js:161
      throw er; // Unhandled 'error' event
      ^

Error: listen EADDRINUSE :::8081
```

Значит наше приложение уже запущено на порту 8081


Управление процессами под Linux
https://www.howtogeek.com/107217/how-to-manage-processes-from-the-linux-terminal-10-commands-you-need-to-know/

**Остановка NodeJS процесса**

Получение id-процесса под Ubuntu

```cli
ps -e|grep node
```

```cli
kill -9 XXXX
```

Где XXXX - номер процесса

http://serverfault.com/questions/256331/how-to-stop-node-js-server

Настройка NodeJS на production'e
https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04

**Настройка виртуального домена для проекта**

В папке проекта создаем config.json

```json
{
"host": "site.local",
"port" : "8081",
"url": "http://site.local:8081",
"serverName": "site.local"
}
```


Для редактирования файла хостов в Ubuntu

```cli
sudo nano /etc/hosts
```

Прописываем

```cli
127.0.0.1    site.local
```

http://www.ainixon.me/how-to-create-virtual-hosts-in-ubuntu/

**Структура папок проекта**


