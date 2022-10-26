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

В каталоге где расположен файл docker-compose.yml следует выполнить команду 

docker-compose up

В итоге получается

![image](https://user-images.githubusercontent.com/68746298/197971216-ab821508-20d5-4434-893f-8dbfed8f25e7.png)

База старовала, стек готов

![image](https://user-images.githubusercontent.com/68746298/197972176-0f902767-2910-44c7-937a-aeb0121c96ea.png)
