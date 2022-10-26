Пример установки стека Prometheus+Grafana для мониторинга базы данных Postgress

Для развертывания стека используется Docker Compose, который уже входит в поставку Windows Docker Desktop. 
Сценарий сборки описан в файле docker-compose.yml.
Устанавливаются четыре компонента
 - база данных postrgress версии 14
 - postgress-exporter
 - prometheus
 - grafana
 
![image](https://user-images.githubusercontent.com/68746298/197963633-0d9cdfd0-16c1-455f-9a99-b8f72101c17e.png)

Предварительно, в каталоге с %USERPROFILE% следует создать директорию 
%USERPROFILE%\postgress\prometheus\
и скопировать туда файл prometheus.yml 
Если содать каталог в другом месте не будет производится правильное мапирование виртуального диска в Docker на физическое устройство (ошибка Docker Compose) 

