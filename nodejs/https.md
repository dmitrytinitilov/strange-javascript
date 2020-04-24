**Вариант с обновлением уже готовых настроек**

```
./cerbot-auto renew
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
Чтобы открыть в nano, а не в VIM

```cli
EDITOR=nano crontab -e
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



