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
    
    ![Создание пользователя](https://user-images.githubusercontent.com/109212419/205152349-77e348c0-6102-4c00-a0b6-bb01ead005d4.jpg)

    Предоставление привилегий пользователю test на базу
    
    mysql> GRANT SELECT ON amolokov_db.* to 'test'@'localhost';
    
    ![предоставление прав на базу](https://user-images.githubusercontent.com/109212419/205152451-e402988a-2708-488f-b5f9-a9cb1b36c401.jpg)

    
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
    
    
