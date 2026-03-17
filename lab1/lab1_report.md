University: [ITMO University]
Faculty: [FTMI]
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)
Year: 2026
Group: U4125
Author: Novikov Vladimir Vladimirovich
Lab: Lab1
Date of create: 16.03.2026
Date of finished: 17.03.2026

Работал на Windows через Git Bash.

1.	Установил Docker Desktop (если ещё не стоял, запустил приложение после установки).
2.	Проверил версию: docker --version – вывел актуальную версию 
3.	Запустил тестовый контейнер: docker run hello-world – получил сообщение «Hello from Docker!».
4.	Посмотрел базовые команды: docker images, docker ps, docker ps -a – увидел образ hello-world и контейнер в статусе Exited.
5.	Скачал образ Ubuntu: docker pull ubuntu:latest.
6.	Запустил интерактивный контейнер: docker run -it ubuntu:latest bash → внутри установил curl: apt update && apt install -y curl → проверил curl --version → вышел exit.
7.	Запустил веб-сервер nginx: docker run -d -p 8080:80 --name web-server nginx:alpine → открыл в браузере http://localhost:8080 – увидел «Welcome to nginx!» (смотреть скриншот Welcome to nginx).
8.	Посмотрел логи: docker logs web-server. Подключился внутрь: docker exec -it web-server sh.
9.	Поуправлял контейнерами: docker ps, docker ps -a, docker stop web-server, docker start web-server, docker rm web-server, docker rmi nginx:alpine.
10.	Поработал с томами: docker volume create my-volume Запустил контейнер с томом: docker run -d --name volume-test -v my-volume:/data ubuntu:latest sleep infinity Подключился: docker exec -it volume-test sh → создал файл echo "Hello from volume" > /data/test.txt Удалил контейнер, создал новый с тем же томом → файл остался.

1*

11. Создал папку lab1 внутри репозитория. 
12. В папке lab1 создал файлы:
•	app.py (Flask приложение, возвращает "Hello from Docker!" на /)
•	requirements.txt с Flask==2.0.1
13. Создал Dockerfile по строгим требованиям ТЗ:
•	FROM python:3.9-slim
•	WORKDIR /app
•	RUN apt-get install curl vim
•	COPY requirements.txt и RUN pip install -r requirements.txt
•	COPY app.py
•	RUN useradd appuser UID 1000 + USER appuser
•	EXPOSE 5000
•	ENV FLASK_ENV=production
•	CMD ["python", "app.py"]
14. Первая сборка упала из-за несовместимости Werkzeug (новая версия сломала старый Flask). Добавил в requirements.txt фикс: Werkzeug==2.3.7. 
15. Пересобрал образ: docker build -t my-flask-app . 
16. Запустил контейнер: docker run -d -p 5000:5000 --name flask-container my-flask-app 
17. Проверил: docker ps — контейнер Up docker logs flask-container — увидел * Running on http://0.0.0.0:5000curl http://localhost:5000 — получил Hello from Docker! (и в браузере то же самое).

