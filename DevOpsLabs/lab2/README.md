<h1 align="center">Лабораторная работа №2</h1>
<h2> Основная часть </h2>
<h3> Цель работы </h3>

Написать два Dockerfile – плохой и хороший. Описать все плохие практики
первого Dockerfile и то как они были справлены во втором.

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
