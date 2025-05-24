# Домашнее задание к занятию "«Работа с данными (DDL/DML)»" - `Динейко Алексей`


---

### Задание 1
`Простыня запросов MySQL`

- 1.2. Создание пользователя sys_temp
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';

- 1.3. Запрос на получение списка пользователей в базе данных + скриншот запроса 
SELECT user, host FROM mysql.user;

![Скриншот-1](https://github.com/Neoju5t/WorkingWithData/blob/f0ad8fe0eb9a2566d790d0f1a686c96d28145f8f/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2010.31.15.png)

- 1.4. Выдача всех привилегий пользователю
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';

- Обновление прав
FLUSH PRIVILEGES;

- 1.5. Проверка прав пользователя + скриншот прав пользователя 'sys_temp'
SHOW GRANTS FOR 'sys_temp'@'localhost';

![Скриншот-2](https://github.com/Neoju5t/WorkingWithData/blob/f0ad8fe0eb9a2566d790d0f1a686c96d28145f8f/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2010.33.02.png)

- 1.6. Смена типа аутентификации
ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

- 1.7. Восстановление дампа sakila 
- Создание базы данных
CREATE DATABASE sakila;

- Импорт структуры
USE sakila;
SOURCE /tmp/sakila/sakila-schema.sql;

- Импорт данных
SOURCE /tmp/sakila/sakila-data.sql;

- 1.8. Проверка таблиц + скриншот таблиц
SHOW TABLES;

![Скриншот-3](https://github.com/Neoju5t/WorkingWithData/blob/f0ad8fe0eb9a2566d790d0f1a686c96d28145f8f/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2010.56.45.png)

---

### Задание 2

[Файл excel с первичными ключами таблиц](https://github.com/Neoju5t/WorkingWithData/blob/f0ad8fe0eb9a2566d790d0f1a686c96d28145f8f/img/%D0%A2%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%20%D0%BF%D0%B5%D1%80%D0%B2%D0%B8%D1%87%D0%BD%D1%8B%D1%85%20%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%B8%CC%86.xlsx)

---
