<h1 align="center">Лабораторная работа №3</h1>
<h2> Основная часть </h2>
<h3> Цель работы </h3>

Сделать так, чтобы после пуша в репозиторий автоматически собирался докер образ
и результат его сборки где-то сохранялся.
### Основная часть

Итак, мы написали программу на языке Python, которая генерирует .txt файл на локальной машине, запись в котором меняется в различных коммитах: 

```
import subprocess
import re

#getting sha of last commit
repo_url = 'https://github.com/Di0Zavr/ItmoCloud_lab3'
process = subprocess.Popen(["git", "ls-remote", repo_url], stdout=subprocess.PIPE)
stdout, stderr = process.communicate()
sha = re.split(r'\t+', stdout.decode('ascii'))[0]

with open("output.txt", "w") as f:
	f.write(f"Hello, world!\nYour commit's sha is {sha}")

```

А так же Dockerfile, который запускает этот файл, взяв образ Python:

```
FROM python:3

WORKDIR /app/

COPY . /app/

CMD ["python", "generate_text.py"]
```
Был написан скрипт для GitHub Actions, который срабатывает при пуше в main. В нём прописаны 2 джоба:

1. (generate-text-file) Собрать образ, запустить контейнер, достать из контейнера сгенерированный .txt и добавить его в наш репозиторий через коммит-пуш.
2. (push-on-dockerhub) Авторизоваться на DockerHub и запушить полученный образ на Docker Hub. Для авторизации используются данные, которые прописаны в секрете репозитория.
Здесь `name` - навзание шага в github actions, `uses` - библиотека с помощью которой выполняется шаг, `with` - дополнительные данные
```
name: doing-devops-lab3-stuff

on:
  push:
    branches:
      - main

jobs:
  generate-text-file:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Build the docker image
      run: docker build -t lab3-generating-text .

    - name: Run the docker container and copy output.txt back to the repository
      run: docker run --name my-container lab3-generating-text

    - name: Copy txt file from the container
      run: docker cp my-container:/app/output.txt $GITHUB_WORKSPACE

    - name: Clean up
      run: docker rm my-container

    - name: Commit and push generated output.txt
      run: |
        git config --global user.email "actions@github.com"
        git config --global user.name "GitHub Actions"
        git add output.txt
        git commit -m "Add generated output.txt"
        git push

  push-on-dockerhub:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repo
      uses: actions/checkout@v4

    - name: Login on dockerhub
      uses: docker/login-action@v3
      with:
        username: ${{ secrets.DOCKERHUB_USERNAME }}
        password: ${{ secrets.DOCKERHUB_PASSWORD }}

    - name: Push image on dockerhub
      uses: docker/build-push-action@v5
      with:
        context: .
        push: true
        tags: dio05000/lab3-image:latest
```

Образ на Docker Hub:
 
![image](https://github.com/Di0Zavr/itmo_cloud_2023/assets/42793074/30dc8445-3a9e-4f58-a7d4-1b0499c32e30)

### Вывод:
Мы написали Docker-образ на образе Python:3 и настроили GithubActions, чтобы он создавал контейнер на данном образе и взаимодействовал с его функционалом.


