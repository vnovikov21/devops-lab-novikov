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
1. Создал папку lab3/prometheus и файл prometheus.yml с scrape_interval 15s и таргетами prometheus + node-exporter.
2. Запустил node-exporter (порт 9100) — метрики доступны по curl http://localhost:9100/metrics.
3. Создал том prometheus-data и сеть monitoring.
4. Запустил Prometheus (порт 9090) с монтированием конфига и данных.  
   После фикса пути в Git Bash контейнер стабильно Up, targets в http://localhost:9090/targets — оба UP.
5. Запустил Grafana (порт 3000) с томом grafana-data и паролем admin.
6. В Grafana добавил data source Prometheus (URL: http://prometheus:9090) — Save & Test успешно.
7. Создал дашборд с двумя панелями:
   - CPU usage: rate(node_cpu_seconds_total[5m])
   - Available memory: node_memory_MemAvailable_bytes
8. Тестирование:  
   docker ps — все контейнеры Up  
   http://localhost:9090/targets — оба таргета UP  
   http://localhost:3000 — дашборд отображает метрики хоста



