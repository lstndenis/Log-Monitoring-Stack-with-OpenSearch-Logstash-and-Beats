![Docker](https://img.shields.io/badge/Docker-25.0-blue)
![OpenSearch](https://img.shields.io/badge/OpenSearch-2.19.0-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Log-Monitoring-Stack-with-OpenSearch-Logstash-and-Beats

Это тестовый проект, демонстрирующий:
- Развертывание OpenSearch + Dashboards + Logstash через Docker Compose.
- Сбор логов с помощью Filebeat, Winlogbeat и Syslog.
- Парсинг в ECS (SSH, SUDO, Windows события).
- Настройка алертов (Alerting + Security Analytics).
- Визуализация в OpenSearch Dashboards.

Краткая схема:
* Windows (Winlogbeat) -> Linux VM1 (Logstash (port 5044)) -> Linux VM1 (OpenSearch (port 9200)) <- Linux VM1 (OpenSearch Dashboards (5601))
* Linux VM2 (Filebeat) -> Linux VM1 (Logstash (port 5044))
* Linux VM2 (Syslog) -> Linux VM1 (Logstash (port 5514))

Требования
- Docker и Docker Compose (установлены обоих ВМ с Linux).
- Linux ВМ2 (Ubuntu 22.04+) для отправки syslog и Filebeat.
- Хостовая Windows (для Winlogbeat).
- Открытые порты на первой ВМ: 9200, 5601, 5044, 5514 (TCP/UDP).

## Визуализации и дашборды

Гистограмма успешных SSH-входов по времени:
![SSH успешные входы](screenshots/Рисунок22.png)

Сравнение успешных и неудачных попыток SSH:
![Сравнение SSH](screenshots/Рисунок23.png)

Гистограмма событий sudo:
![Гистограмма sudo](screenshots/Рисунок25.png)

Комбинированный график SSH + sudo:
![SSH + sudo](screenshots/Рисунок26.png)
