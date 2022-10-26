Пример установки стека Prometheus+Grafana для мониторинга базы данных Postgress

Для развертывания стека используется Docker Compose, который уже входит в поставку Windows Docker Desktop. 
Сценарий сборки описан в файле docker-compose.yml.
Устанавливаются четыре компонента
 - база данных postrgress версии 14
 - postgress-exporter
 - prometheus
 - grafana
 
![image](https://user-images.githubusercontent.com/68746298/197963633-0d9cdfd0-16c1-455f-9a99-b8f72101c17e.png)

Предварительно, в каталоге  %USERPROFILE% следует создать директорию 

%USERPROFILE%\postgress\prometheus\
и скопировать туда файл prometheus.yml 

Если создать каталог в другом месте не будет производится правильное мапирование виртуального диска в Docker на физическое устройство (ошибка Docker Compose) 

В каталоге где расположен файл docker-compose.yml следует выполнить команду 

docker-compose up

В итоге получается

![image](https://user-images.githubusercontent.com/68746298/197971216-ab821508-20d5-4434-893f-8dbfed8f25e7.png)

База старовала, стек готов

![image](https://user-images.githubusercontent.com/68746298/197974385-e0f67155-9f5a-4370-be01-194e6ef91b4d.png)

Можно проверить работу postrgess-exporter

http://localhost:9090/targets

![image](https://user-images.githubusercontent.com/68746298/197975032-aedce9fe-ae2e-41af-9e6b-cb8ca6ba1b74.png)

Можно переходить к визуализации метрик, пользователь admin/admin

http://localhost:3000

![image](https://user-images.githubusercontent.com/68746298/197975815-2df2a14d-24bb-4d08-ac5b-da59a6034f37.png)

Далее необходимо добавить в Grafana новый источник данных - Prometheus, который уже собирает метрики базы данных Postgress с помощью Postgress-Exporter

![image](https://user-images.githubusercontent.com/68746298/197978044-e4bc67e1-2b1a-46c7-a0d9-0ff8244d0111.png)

В строке соединения (HTTP:URL) необходимо указать адрес http://prometheus:9090  

![image](https://user-images.githubusercontent.com/68746298/197980070-976c210b-5ad1-4c01-811a-2e9cae3d2f48.png)

Перед сохранением можно протестировать работоспособность источника (Save&Test) 

Осталось только импортировать соответвующий dashboard для отображения метрик,которые  можно найти - 

https://grafana.com/grafana/dashboards/?search=postgres

Далее неоходимо импортировать понравившийся 

![image](https://user-images.githubusercontent.com/68746298/197983168-516379ab-d194-4aef-b705-f674987db186.png)

указав соответсвующий ID 

![image](https://user-images.githubusercontent.com/68746298/197991358-f3c3a26d-8e52-40fe-b815-b21a475ad3ab.png)

и источник данных.

![image](https://user-images.githubusercontent.com/68746298/197984087-62fa3a96-5709-40d9-b667-4d0dbb064437.png)


Осталось открыть импортированный Dashboard

![image](https://user-images.githubusercontent.com/68746298/197992170-4d1d4e9b-3b69-4efc-b549-6ed2e2c93b4d.png)



Создано по мотивам публикации
https://dev.to/nelsoncode/how-to-monitor-posgresql-with-prometheus-and-grafana-docker-24c8
