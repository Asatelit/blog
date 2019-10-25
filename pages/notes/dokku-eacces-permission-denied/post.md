---
title: 'Dokku: 413 Request Entity Too Large'
color: white
truncate: 40
date: '17:30 25-10-2019'
taxonomy:
    category: Notes
    tag:
        - dokku
        - faq
---

#### Проблема

Ошибка "Errno::EACCES (Permission denied)" при попытке загрузить файл на инстанс с Dokku.


#### Причина

Скорее всего нужно разобраться с Persistent Storage - этот плагин синхронизирует внешние ресурсы инстанса с контейнером Dokku.


#### Решение

[Persistent Storage](http://dokku.viewdocs.io/dokku/advanced-usage/persistent-storage/)


#### Примечания

Для версий Dokku старше 0.7.1 владелецем внешнего ресурса (директории) должен быть пользователь 32767:
```bash
chown -R 32767:32767 /var/lib/dokku/data/storage/YOUR_APP_NAME
```
