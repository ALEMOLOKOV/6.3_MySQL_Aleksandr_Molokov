# 6.3_MySQL_Aleksandr_Molokov

ЗАДАНИЕ 1

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

Количество записей с price > 300 (в базе только одна запись подходит под условие (2,'My little pony',500))

![6 3 Задание 1 price 300](https://user-images.githubusercontent.com/109212419/204895497-8afbb500-24a7-48fb-915f-f60d45e788ee.jpg)


ЗАДАНИЕ 2

Создание пользователя test с паролем test-pass (пришлось заходить под пользователем root, с паролем Hoax2z2a, amolokov ошибка прав доступа) 

    CREATE USER 'test'@'localhost' 
    IDENTIFIED WITH mysql_native_password BY 'test-pass'
    WITH MAX_CONNECTIONS_PER_HOUR 100
    PASSWORD EXPIRE INTERVAL 180 DAY
    FAILED_LOGIN_ATTEMPTS 3 PASSWORD_LOCK_TIME 2
    ATTRIBUTE '{"first_name":"James", "last_name":"Pretty"}';
    
    
   ![Создание пользователя](https://user-images.githubusercontent.com/109212419/205369068-09ae31d9-799d-462f-a347-771281f9a97a.jpg)

    Предоставление привилегий пользователю test на базу
    
    mysql> GRANT SELECT ON amolokov_db.* to 'test'@'localhost';
    
    
   ![предоставление прав на базу](https://user-images.githubusercontent.com/109212419/205369124-29225c6e-74b1-4379-b4d1-aaa739d77dd5.jpg)

    
    Данные по пользоввателю
    
    mysql> SELECT * from INFORMATION_SCHEMA.USER_ATTRIBUTES where USER = 'test';
    
   ![данные по пользователю](https://user-images.githubusercontent.com/109212419/205143233-ffb5aab1-82f0-4086-a483-354800ca83f9.jpg)
 

    ЗАДАНИЕ 3
    
    Установка профилирования и вывод команд
    
    SHOW PROFILE - отображение последних команд отправленных на сервер
    
   ![установка профилирования и вывод команд](https://user-images.githubusercontent.com/109212419/205151782-3dec4dac-3a32-4e88-be63-e6fde1539863.jpg)

    Поиск используемого в БД engin
    
    mysql> SELECT TABLE_NAME, ENGINE FROM information_schema.TABLES where TABLE_SCHEMA = 'amolokov_db';
    
   ![engin БД](https://user-images.githubusercontent.com/109212419/205151653-99a94a6c-f8d5-4334-85cc-fd7d1d1bc2e0.jpg)

    
    Изменение engin в БД
    
    mysql> ALTER TABLE orders ENGINE = MyISAM;
    
    mysql> ALTER TABLE orders ENGINE = InnoDB;
    
   ![изменение engin БД](https://user-images.githubusercontent.com/109212419/205151569-8cc9d497-47f0-430d-9f5d-ec5de21111dc.jpg)

       
    
    ЗАДАНИЕ 4
    
    Файл my.cnf разположение etc/my.cnf (файл my.cnf располагался в /etc/my.cnf)
    
   ![файл my cnf](https://user-images.githubusercontent.com/109212419/205154710-592c2624-15ac-41f9-a822-7e3bba8f0ae7.jpg)
    
    Добавление данныхв файл my.cnf (создал файл adding_to_my.cnf, добавил в него параметры из ТЗ, далее записал их в файл my.cnf, 
    пробовал открыть через nano и vim, ошибка команда не найдена)
    
    bash-4.4# cat adding_to_my.cnf >> my.cnf
    
    Файл с изменениями
    
   ![my cnf with changing](https://user-images.githubusercontent.com/109212419/205159834-d2d42293-01b7-47ec-879d-75701d39c5d9.jpg)

    






    
