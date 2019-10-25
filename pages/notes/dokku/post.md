---
title: 'Dokku: 413 Request Entity Too Large'
color: white
truncate: 40
date: '17:29 25-10-2019'
taxonomy:
    category: Idea
    tag:
        - dokku
        - nginx
        - faq
---

### Проблема

Ошибка '413 Request Entity Too Large' при попытке загрузить файл весом больше чем один мегабайт на инстанс с Dokku.

### Причина

Дефолтный Nginx конфиг Dokku ограничивает максимальный размер до 1 Мбайта. 

### Решение

Переходим в директорию приложения Dokku с настройками nginx: 
```bash
/home/dokku/YOUR_APP_NAME/nginx.conf.d/
```
Если в приложении нет директории nginx.conf.d, нужно создать ее:
```bash
mkdir /home/dokku/YOUR_APP_NAME/nginx.conf.d/
```

Теперь нужно создать файл upload.conf со следующей инструкцией:
```bash
echo 'client_max_body_size 50m;' > /home/dokku/YOUR_APP_NAME/nginx.conf.d/upload.conf
```

Владельцем файла должен быть dokku:
```bash
chown dokku:dokku /home/dokku/node-js-app/nginx.conf.d/upload.conf
```

Дальше рестарт и все готово:
```bash
service nginx reload
```
