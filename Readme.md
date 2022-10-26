Пример установки стека Prometheus+Grafana для мониторинга базы данных Postgress

Для развертывания стека используется Docker Compose, который уже входит в поставку Windows Docker Desktop. 
Сценарий сборки описан в файле docker-compose.yml.
Устанавливаются четыре компонента
 - база данных postrgress версии 14
 - postgress-exporter
 - prometheus
 - grafana
 ![image](https://user-images.githubusercontent.com/68746298/197962153-fbe0978b-f571-45c9-b9be-12acec6a31ad.png)

