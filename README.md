# 6.3_MySQL_Aleksandr_Molokov

Задание 1

Развертывание MySQL 8.0 

docker-compose.yaml

version: '3.7'
services:
  db:
    image: mysql:8
    restart: always
    environment:
      MYSQL_DATABASE: 'amolokov_db'
      MYSQL_USER: 'amolokov'
      MYSQL_PASSWORD: 'Hoax1z1a'
      MYSQL_ROOT_PASSWORD: 'Hoax2z2a'
    volumes:
      - mysql-db:/var/lib/mysql
volumes:
  mysql-db:

Запуск

vagrant@vagrant:~/docker/volumes/mysql$ sudo docker-compose up -d

![6 3 задание 1 развертывание](https://user-images.githubusercontent.com/109212419/204364748-7312886e-9569-489e-bbbe-d7e24d530f4a.jpg)

Копирование бэкапа в контейнер

vagrant@vagrant:~/docker/volumes/mysql$ sudo docker cp test_dump.sql mysql_db_1:/var 




Запуск командной строки в контейнере и восстановление БД из бэкапа

![6 3 Задание 1 развертывание mysql с восстановленной базой](https://user-images.githubusercontent.com/109212419/204371117-443cea71-5c46-4414-8262-b64145c656fd.jpg)


Команда \h

![6 3 Задание 1 флаг h](https://user-images.githubusercontent.com/109212419/204894542-fc4b1fba-f67a-4959-aca4-bbcc48ef3f15.jpg)


Команда для вывода статуса БД

![6 3 Задание 1 Статус БД](https://user-images.githubusercontent.com/109212419/204894119-339f792d-15d5-417f-b290-60e73d649c16.jpg)

Проверка списка таблиц БД

![6 3 Задание 1 Список таблиц](https://user-images.githubusercontent.com/109212419/204894895-1626f373-61ef-41fe-8dce-3b0c005ae17f.jpg)

Количество записей с price > 300

![6 3 Задание 1 price 300](https://user-images.githubusercontent.com/109212419/204895497-8afbb500-24a7-48fb-915f-f60d45e788ee.jpg)










