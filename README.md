# Домашнее задание к занятию "«SQL. Часть 2»" - `Динейко Алексей`

---

### Задание 1

`Запрос для получения информации о магазине с более чем 300 покупателями`

SELECT 
    s.last_name AS "Surname",
    s.first_name AS "Name",
    city.city AS "Store sity",
    COUNT(c.customer_id) AS "Number of buyers"
FROM 
    store st
INNER JOIN 
    staff s ON st.store_id = s.store_id
INNER JOIN 
    address a ON st.address_id = a.address_id
INNER JOIN 
    city ON a.city_id = city.city_id
INNER JOIN 
    customer c ON st.store_id = c.store_id
GROUP BY 
    st.store_id, s.staff_id, city.city
HAVING 
    COUNT(c.customer_id) > 300;

![Скриншот-1](https://github.com/Neoju5t/SQL-vol.2/blob/0433500c76e82ee736b56325ec9a6e3179559826/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2014.40.38.png)

---

### Задание 2

`Запрос для получения количества фильмов с продолжительностью больше средней`

SELECT 
    COUNT(*) AS "Number of films"
FROM 
    film
WHERE 
    length > (SELECT AVG(length) FROM film);

![Скриншот-2](https://github.com/Neoju5t/SQL-vol.2/blob/0433500c76e82ee736b56325ec9a6e3179559826/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2014.42.23.png)

---

### Задание 3

`Запрос для получения месяца с наибольшей суммой платежей и количества аренд`

SELECT 
    DATE_FORMAT(p.payment_date, '%Y-%m') AS "Month",
    SUM(p.amount) AS "sum of payment",
    COUNT(r.rental_id) AS "Number of rents"
FROM 
    payment p
INNER JOIN 
    rental r ON p.rental_id = r.rental_id
GROUP BY 
    DATE_FORMAT(p.payment_date, '%Y-%m')
ORDER BY 
    SUM(p.amount) DESC
LIMIT 1;

![Скриншот-3](https://github.com/Neoju5t/SQL-vol.2/blob/0433500c76e82ee736b56325ec9a6e3179559826/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2014.45.22.png)

---
