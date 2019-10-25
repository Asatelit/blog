---
title: 'Деплой create-react-app проекта на Dokku в виде статического сайта'
color: white
truncate: 40
date: '17:29 25-10-2019'
taxonomy:
    category: Notes
    tag:
        - dokku
        - nginx
        - create-react-app
        - faq
---

Настройки для CRA-проекта:
- Добавить в корень проекта пустой файл ```.static```.
- Добавить в корень проекта файл ```.buildpacks``` со следующем содержанием:
```
https://github.com/heroku/heroku-buildpack-nodejs
https://github.com/dokku/buildpack-nginx
```
- Добавить раздел в package.json инструкцию "engines":
```json
"engines": {
  "node": ">=12.0",
  "yarn": ">=1.10"
},
```
- Добавить в раздел "scripts" файла package.json следующую инструкцию:
```json
"dokku": {
  "predeploy": "yarn build"
} 
```

После успешной загрузки проекта в Dokku в терминале инстанса нужно прописать:
```bash
dokku config:set blog NGINX_ROOT=build/
```
