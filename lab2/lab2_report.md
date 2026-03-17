University: [ITMO University]
Faculty: [FTMI]
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)
Year: 2026
Group: U4125
Author: Novikov Vladimir Vladimirovich
Lab: Lab2
Date of create: 16.03.2026
Date of finished: 17.03.2026

Работал на Windows через Git Bash.
1.	Скопировал файлы из первой лабораторной в папку lab2: app.py, requirements.txt, Dockerfile (из lab1).
2.	Создал аккаунт на Docker Hub под логином vladimirnovikov42. Создал репозиторий my-flask-app (полное имя: vladimirnovikov42/my-flask-app). Сделал его публичным.
3.	Добавил секреты в настройках репозитория GitHub (Settings → Secrets and variables → Actions):
-	DOCKER_USERNAME: vladimirnovikov42
-	DOCKER_PASSWORD: пароль от аккаунта Docker Hub (сначала был токен доступа, но выдавал ошибку при build, поэтому позже изменил на пароль)
4.	Создал папку .github/workflows и файл docker-build.yml с пайплайном:
-	запуск при пуше в main
-	runner: ubuntu-latest
-	checkout кода
-	настройка Docker Buildx
-	логин в Docker Hub через секреты
-	сборка и пуш образа vladimirnovikov42/my-flask-app:latest
-	простой шаг echo для имитации деплоя.
5.	Закоммитил и запушил изменения: git add .github/workflows/docker-build.yml git commit -m "Lab 2: GitHub Actions CI/CD pipeline" git push origin main
6.	Пайплайн запустился автоматически в разделе Actions. Все шаги прошли зелёным:
-	Checkout code
-	Set up Docker Buildx
-	Login to Docker Hub
-	Build and push image (образ успешно запушен)
-	Deployment step (placeholder)
7.	Проверил Docker Hub: https://hub.docker.com/r/vladimirnovikov42/my-flask-app


