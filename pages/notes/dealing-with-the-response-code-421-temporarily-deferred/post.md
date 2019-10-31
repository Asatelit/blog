---
title: 'Избавление от ResponseCode 421 (Temporarily Deferred)'
color: white
truncate: 40
date: '17:30 31-10-2019'
taxonomy:
    category: Notes
    tag:
        - zoho
        - email
        - smtp
        - howto
---

#### Проблема

Почтовый сервер отклоняет или задерживает пересылку электронной почты отправляемой с локалхоста через SMTP протокол.
```
ResponseCode 421, 4.7.0 Temporarily Deferred
```

#### Решение

Необходимо добавить следующую TXT запись в настройках DNS сервера:
```
_dmarc.your.domin IN TXT v=DMARC1; p=none; sp=none; rua=mailto:mailbox@your.domain
```
Где:
- ```p=none``` - политика предписывающая не принимать никаких действий по отношению к подозрительным сообщениям,
- ```sp=none``` - те же что и предыдущий пункт, но уже для поддоменов,
- ```rua=mailto:mailbox@your.domain``` - задает почтовый адрес на который раз в сутки будут приходить отчеты в XML.

В любом случае, стоит ознакомиться с этим вопросом более внимательно и просмотреть нижеприведенные материалы.

#### Ссылки
- [Node.js version manager for Windows](https://emailmatrix.ru/blog/what-is-dmarc/)
- [HowTo: DMARC](https://habr.com/ru/post/253705/)
- [Настройка DKIM/SPF/DMARC записей или защищаемся от спуфинга](https://habr.com/ru/post/322616/)
