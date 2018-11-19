# Работа с Git
```cmd
git init
```
git init - инициализирует репозиторий

```cmd
git clone https://github.com/shorten/js.git
```

```cmd
git status
```
покажет нам состояние системы

```cmd
git add <filename>
```

добавит один файл

```cmd
git add *
```

Удаление папки из индекса, которую по ошибке добавили

```cmd
git rm -r --cached path_to_your_folder/
```

Добавим данные из индекса в HEAD
```cmd
git commit -m "текст вашего сообщения о том, что изменено"
```
Если выдается сообщение
_please tell me who you are_

то выполняем

```cmd
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

**Залитие файлов на Github**

Добавим адрес удаленного хранилища
```cmd
git remote add origin <server>
```

Вместо <server> берем адрес Вашего репозитория на Github

Можно проверить установилось ли хранилище с помощью команды
```cmd
git remote show origin
```

Отправим данные на удаленное хранилище из ветки master
```cmd
git push origin master
```

добавит все файлы из директории

**.gitignore**

Те папки, которые мы не хотим видеть в репозитории, например node_modules нужно добавить в файл .gitignore

Чтобы посмотреть какие файлы и папки игнорируются
```cmd
git status --ignored
```
Чтобы узнать каким правилом игнорируется данный файл
```cmd
git check-ignore -v filename
```

**Добавление пустой папки в репозиторий**

Полностью пустые директории игнорируются Git'ом, поэтому можно создать директорию с пустым файлом .gitkeep

[Вариант с .gitignore](https://stackoverflow.com/questions/115983/how-can-i-add-an-empty-directory-to-a-git-repository) приведет к тому, что в дальнейшем папки добавленные в проект будут также игнорироваться.

**README.md**

Шпаргалка по Markdown
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

**Синхронизация локального и удаленного(remote) репозиториев**

Просмотр разницы между локальной веткой и удаленной(remote)

```cmd
git diff master origin/master
```
Для выхода из сравнения нужно нажать q

**Если нужно перезалить локальные файлы файлами из репозитория**

```cmd
git fetch --all
Then, you have two options:

git reset --hard origin/master
OR If you are on some other branch:

git reset --hard origin/<branch_name>
```
**Создание новой ветки и перенос ее на Github**

```cmd
git checkout -b <branch>
```

Делаем коммит измененных файлов

Добавляем ветку еще и на Github
```cmd
git push -u origin <branch>
```

Скачивание проекта из нужной ветки

```cmd
git clone http://whatever.git -b branch-name
```

**Краткий стартовый мануал по Git**
http://rogerdudler.github.io/git-guide/

**Cheatsheet по различным ситуациям**
https://gist.github.com/jedmao/5053440


**Работа с ветками**

О feature branch
https://bocoup.com/blog/git-workflow-walkthrough-feature-branches




**Workflow**
https://confluence.atlassian.com/bitbucket/workflow-for-git-feature-branching-814201830.html

https://www.atlassian.com/git/tutorials/comparing-workflows

**Набор красочных скетчей по Git  (Meow Git или Git Puss)**
https://twitter.com/girlie_mac/status/905270297128865792


**Очень емкий мануал по всяким проблемным ситуациям с git**
http://ohshitgit.com

**Заливка проекта на github**<BR>
http://gotit.com.ua/administration-systems-i-services/kak-zalit-proekt-na-github-com.html

**Создание ssh-ключа**<BR>
https://docs.joyent.com/public-cloud/getting-started/ssh-keys/generating-an-ssh-key-manually/manually-generating-your-ssh-key-in-windows

**Создание ветки на git**<BR>
https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches

**Советы по Git'у от Mail.ru**<BR>
https://habrahabr.ru/company/mailru/blog/267595/


**Полезное чтиво:**

1. Ежедневная работа с Git
https://habrahabr.ru/post/174467/

2. Интерактивный тур по Git'у
https://githowto.com/ru

3. Почему нужно перестать использовать Git rebase
https://habrahabr.ru/company/mailru/blog/340558/

4. Курс по git с кучей заданий
http://gitimmersion.com

**Практика**

1. Создать новую ветку feature_readme, сделать  файл README.md, добавить его в эту ветку. Объединить ветку с веткой master, залить на github.


