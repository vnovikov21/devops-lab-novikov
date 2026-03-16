University: [ITMO University]
Faculty: [FTMI]
Course: [Введение в веб технологии](https://itmo-ict-faculty.github.io/introduction-in-web-tech/)
Year: 2026
Group: U4125
Author: Novikov Vladimir Vladimirovich
Lab: Lab0
Date of create: 16.03.2026
Date of finished: 16.03.2026

Работал на Windows через Git Bash.

1.	Создал новый аккаунт на GitHub (@vnovikov21). Добавил новый SSH-ключ (ed25519), добавил его в настройки GitHub
2.	Создал репозиторий https://github.com/vnovikov21/devops-lab-novikov Выбрал в настройках создать ридми, не выбрал лицензию. 
3.	Склонировал его к себе: git clone git@github.com:vnovikov21/devops-lab-novikov.git Зашёл в папку.
4.	Настроил git, потому что первый коммит ругался: указал имя и почту (ту, что на GitHub).
5.	Сделал README.md, написал туда, что это лабы по DevOps, оставил ссылку на свой GitHub, email и набросал примерный план по лабам исходя из заданий
6.	Создал .gitignore, внес туда стандартный набор для Windows 
7.	Создал ветку develop: git checkout -b develop
8.	Написал CONTRIBUTING.md – коротко про то, как предлагается участвовать
9.	Добавил все три файла, закоммитил: git commit -m "Initial project setup" (была ошибка коммитинга, указал автора и почту и ошибка ушла)
10.	Отправил ветку: git push origin develop
11.	Зашёл в браузер, создал Pull Request из develop в main. Написал заголовок и описание, что именно добавил.
12.	Смержил PR в браузере, потом удалил ветку develop (кнопка появилась после мержа).
13.	Переключился на main, подтянул изменения и удалил старую ветку: git branch -d develop

