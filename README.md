# Домашнее задание к занятию "«SQL. Часть 1»" - `Динейко Алексей`

---

### Задание 1

`Запрос для получения уникальных названий районов`

SELECT DISTINCT district 
FROM address 
WHERE 
    district LIKE 'K%a' 
    AND district NOT LIKE '% %';

![Скриншот-1](https://github.com/Neoju5t/SQL-vol.1/blob/aad1f8b09cb0868474aa000fc8fbebc500c1fd6e/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2011.51.29.png)

---

### Задание 2

`Запрос для получения платежей в заданный период`

SELECT *
FROM payment 
WHERE 
    payment_date BETWEEN '2005-06-15 00:00:00' AND '2005-06-18 23:59:59' 
    AND amount > 10.00;

![Скриншот-2](https://github.com/Neoju5t/SQL-vol.1/blob/caba40730d61d787cd21e30f7bb2afbfcd6e9d8a/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2011.52.05.png)

---

### Задание 3

`Запрос для получения последних пяти аренд`

![Скриншот-3](https://github.com/Neoju5t/SQL-vol.1/blob/caba40730d61d787cd21e30f7bb2afbfcd6e9d8a/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2011.52.26.png)

---

### Задание 4

`Запрос для получения активных покупателей Kelly/Willie`

![Скриншот-4](https://github.com/Neoju5t/SQL-vol.1/blob/caba40730d61d787cd21e30f7bb2afbfcd6e9d8a/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2011.52.44.png)

---
