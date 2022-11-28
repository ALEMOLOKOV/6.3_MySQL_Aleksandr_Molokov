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

vagrant@vagrant:~/docker/volumes/mysql$ sudo docker cp test_dump.sql mysql_db_1:/var/tmp/test_dump.sql 

![6 3 Задание 1 Копирование бэкапа](https://user-images.githubusercontent.com/109212419/204370596-ea735491-04d7-46b8-93f6-dd99d7f338a7.jpg)


Запуск командной строки в контейнере и восстановление БД из бэкапа

![6 3 Задание 1 развертывание mysql с восстановленной базой](https://user-images.githubusercontent.com/109212419/204371117-443cea71-5c46-4414-8262-b64145c656fd.jpg)

Не получается восстановиться из бэкапа только запуск созаднной базы amolokov_db

![6 3 Задание 1 не получается восстановиться из бэкапа](https://user-images.githubusercontent.com/109212419/204371753-08f1754d-6ce0-42f9-98c7-97bb118db7df.jpg)






