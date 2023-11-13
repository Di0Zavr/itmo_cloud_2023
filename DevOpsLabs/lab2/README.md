<h1 align="center">Лабораторная работа №2</h1>
<h2> Основная часть </h2>
<h3> Цель работы </h3>

Написать два Dockerfile – плохой и хороший. Описать все плохие практики
первого Dockerfile и то как они были исправлены во втором.

### Плохой Dockerfile💩

```
FROM ubuntu:latest
# Create app directory
WORKDIR /usr/src/app
RUN apt-get update && apt-get install -y \
    apt-utils \
    mesa-utils \
    nano \
    apache2
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
RUN npm install
# If you are building your code for production
# RUN npm ci --omit=dev
# Bundle app source
COPY .. .
EXPOSE 8080
CMD [ "node", "server.js" ]
```
Что, собственно, плохо?

1) Использован тег `latest`. Это может быть непредсказуемым и потенциально нестабильным, так как "latest" будет изменяться при выпуске новых версий.

2) Использован избыточный образ `Ubuntu` вместо достаточного `Node.js`. Это увеличивает объём образа и увеличивает количество шагов для установки.
   
3) Устанавливаются пакеты `mesa-utils`, `nano`, и `apache2`, которые не нужны для работы Node.js приложения. Это увеличивает размер образа и количество лишних зависимостей.


### Хороший Dockerfile✨

```
FROM node:18
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
RUN npm install
# If you are building your code for production
# RUN npm ci --omit=dev
# Bundle app source
COPY . .
EXPOSE 8080
CMD [ "node", "server.js" ]
```

Как мы устранили недочёты?

 1) Указали конкретную версию Node.js

 2) Использовали образ `Node.js`

 3) Убрали лишние установки пакетов


### Плохие пракитики по использованию контейнера

 1) Использовать контейнер как ВМ. Контейнер это не виртуалка - не стоит обновлять пакеты, приложения внутри контейнера, подключаться по ssh к контейнеру чтобы, например, перенастроить некоторый конфиг.

 2) Запускать контейнер с root-правами. Если всплывёт уязвимость, взломщик может получить root-права и сделать какую-нибудь каку.

### Вывод

Выполнив данную лабораторную работу мы познакомились с написанием Dockerfile, узнали о некоторых плохих практиках при их проектировании и путях создания более эффективных контейнеров.
