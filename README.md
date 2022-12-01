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

Количество записей с price > 300

![6 3 Задание 1 price 300](https://user-images.githubusercontent.com/109212419/204895497-8afbb500-24a7-48fb-915f-f60d45e788ee.jpg)


ЗАДАНИЕ 2

Создание пользователя test с паролем test-pass

    CREATE USER 'test'@'localhost' 
    IDENTIFIED WITH mysql_native_password BY 'test-pass'
    WITH MAX_CONNECTIONS_PER_HOUR 100
    PASSWORD EXPIRE INTERVAL 180 DAY
    FAILED_LOGIN_ATTEMPTS 3 PASSWORD_LOCK_TIME 2
    ATTRIBUTE '{"first_name":"James", "last_name":"Pretty"}';
    
    ![Создание пользователя](https://user-images.githubusercontent.com/109212419/205141915-3ce9b323-c6ba-458c-bb22-989d3badd279.jpg)
    
    Предоставление привилегий пользователю test на базу
    
    mysql> GRANT SELECT ON amolokov_db.* to 'test'@'localhost';
    
    ![предоставление прав на базу](https://user-images.githubusercontent.com/109212419/205142678-89f1ce52-6ca5-44e7-9540-1a7ac2091fdd.jpg)
    
    Данные по пользоввателю
    
    mysql> SELECT * from INFORMATION_SCHEMA.USER_ATTRIBUTES where USER = 'test';
    
   ![данные по пользователю](https://user-images.githubusercontent.com/109212419/205143233-ffb5aab1-82f0-4086-a483-354800ca83f9.jpg)
 

    ЗАДАНИЕ 3
    
    Установка профилирования и вывод команд
    
    SHOW PROFILE - отображение последних команд отправленных на сервер
       
    ![установка профилирования и вывод команд](https://user-images.githubusercontent.com/109212419/205151038-e9348b01-1552-4f22-9f71-5cdc1325b675.jpg)

    
    Поиск используемого в БД engin
    
    mysql> SELECT TABLE_NAME, ENGINE FROM information_schema.TABLES where TABLE_SCHEMA = 'amolokov_db';
    
    ![engin БД](https://user-images.githubusercontent.com/109212419/205151068-6d28abba-3ddc-45ea-975e-685f6fda35ee.jpg)

    Изменение engin в БД
    
    mysql> ALTER TABLE orders ENGINE = MyISAM;
    
    mysql> ALTER TABLE orders ENGINE = InnoDB;
    
    ![изменение engin БД](https://user-images.githubusercontent.com/109212419/205151147-805819b5-a529-4f7f-8b83-00bddeea0a15.jpg)

    
    
    ЗАДАНИЕ 4
    
    









    











