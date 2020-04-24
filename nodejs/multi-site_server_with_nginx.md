# Настройка нескольких nodejs-сайтов на одном сервере

Установка nginx

```cmd
 sudo apt-get update
 sudo apt-get install nginx
```

Далее создаем директорию sites-available в папке \etc\nginx

```cmd
cd \etc\nginx
mkdir sites-available
```

В папке sites-available Создаем файл your-site.com.conf со следующим наполнением

```json
server {
  listen 80;

  server_name your-site.com;

  location / {
      proxy_pass http://localhost:9091;
  }
}
```

Для Windows в файле nginx.conf добавляем строчку

```
include sites/*.conf;
```

И добавляем конфигурацию в папку sites


Заставляем nginx перечитать конфигурацию

```
nginx -s reload
```

Либо полностью перезапускаем nginx

```
service nginx restart
```

Остается запустить nodejs-процесс на порту 9091 через pm2

```
pm2 start app.js
```

Запуск pm2-процесса с определенным названием

```
pm2 start app.js --name tomagosha
```

Просмотр текущего состояния процессов

```
pm2 status
```

Перезапуск процесса с заданным названием

```
pm2 restart tomagosha
```

Остановка процесса с заданным именем

```
pm2 stop tomagosha
```

Чтобы посмотреть логи процессов

```
pm2 logs
```

**Настройка https-сертификата**

https://certbot.eff.org/lets-encrypt/centos6-nginx

Находим certbot-auto

```
sudo ./certbot-auto --nginx -d yourdomain.com -d www.yourdomain.com
```
Перезапускаем nginx

```
nginx -s reload
```

Если настроете всё правильно, то в nginx/sites-available получите


```nginx
 server {

  server_name yourdomain.com;

  location / {
      proxy_pass http://localhost:4032;
  }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem; # managed$
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem; # manag$
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}



server {

    if ($host = yourdomain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


  listen *:80;
  server_name yourdomain.com;
  proxy_set_header Host yourdomain.com;
  location / {
    rewrite ^(.*)$ https://yourdomain.com$1 permanent;
  }


} 

```

**Настройка cron для обновления сертификата**

Чтобы узнать все текущие задачи набираем в командной строке

```cli
crontab -l
```

Для редактирования заданий нажимаем

```cli
crontab -e
```

Синтаксис задания

* * * * *
| | | | |
| | | | +----- Дни недели (диапазон: 1-7)
| | | +------- Месяцы     (диапазон: 1-12)
| | +--------- Дни месяца (диапазон: 1-31)
| +----------- Часы       (диапазон: 0-23)
+------------- Минуты     (диапазон: 0-59) 


Вариант с пред-запуском и пост-запуском
```cli
0 2 * * * /home/user/certbot-auto renew --pre-hook "service nginx stop" --post-hook "service nginx start"
```

**Полезное чтиво:**

1. Как отображать все cron jobs
https://www.liquidweb.com/kb/how-to-display-list-all-jobs-in-cron-crontab/

2. Синтаксис cron'a
http://www.softtime.ru/forum/read.php?id_forum=1&id_theme=30789



**Полезное чтиво:**

1. Начальная настройка
http://devacademy.ru/posts/nginx-ubuntu-1404/

2. Установка на CentOS
https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7

3. Вариант установки с PM2 
https://www.justinsilver.com/technology/node-js-pm2-nginx-redis-centos-7/

4. Настройка перенаправления на nodejs-процесс на определенном порту
https://toster.ru/q/304044

5. Настройка связки nginx - nodejs
https://gist.github.com/tomasevich/a2fe588c451c5a192893e6521a813020

6. Еще вариант использования nginx-nodejs
https://kuroikaze85.wordpress.com/2010/01/19/using-nginx-with-node-js/

7. Настройка letsencrypt-сертификата через certbot
https://certbot.eff.org/lets-encrypt/centos6-nginx

8. Работа с certbot с nginx и Ubuntu
https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04