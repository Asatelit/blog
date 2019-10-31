---
title: 'Устанавливаем несколько версий Node.js с помощью nvm в Windows'
color: white
truncate: 40
date: '17:29 25-10-2019'
taxonomy:
    category: Notes
    tag:
        - nodejs
        - windows
        - faq
---

#### Проблема

Необходимо выполнить быстрое переключении установленной версии Node.js. 

#### Решение

Скачиваем и устанавливаем Node.js version manager for Windows отсюда. https://github.com/coreybutler/nvm-windows/releases
Дальше, в коммандной строке, устанавливаете необходимую вам версию ноды:  
```bash
nvm install 10.12.7 64
```

Теперь можно активировать установленный инстанс:
```bash
nvm use 10.17.0
```

Проверяем результат:
```bash
node --version
```

Готово. В дальнейшем переключаем инстансы по мере необходимости:
```bash
nvm list
nvm use 12.13.0
```
