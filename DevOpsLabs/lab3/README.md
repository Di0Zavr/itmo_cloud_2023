<h1 align="center">Лабораторная работа №3</h1>
<h2> Основная часть </h2>
<h3> Цель работы </h3>

Сделать так, чтобы после пуша в репозиторий автоматически собирался докер образ
и результат его сборки сохранялся.

```
FROM python:3

WORKDIR /app/

COPY . /app/

CMD ["python", "generate_text.py"]
```

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
