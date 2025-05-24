# Домашнее задание к занятию "«Индексы»" - `Динейко Алексей`

---

### Задание 1

`Запрос для получения процентного отношения размера индексов к общему размеру таблиц`

```
SELECT 
    ROUND(
        (SUM(INDEX_LENGTH) / (SUM(DATA_LENGTH) + SUM(INDEX_LENGTH))) * 100, 
        2
    ) AS index_ratio_percent
FROM 
    information_schema.TABLES 
WHERE 
    TABLE_SCHEMA = 'sakila';
```

`Скриншот запроса и результат процентного отношения размера индексов к общему размеру таблиц:`
![Скриншот-1](https://github.com/Neoju5t/Index/blob/8f587b7e62134bcffdf97ebe3ce55d32fc53b632/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2015.16.35.png)

---

### Задание 2

`Анализ и оптимизация запроса`

Исходный запрос:

```
EXPLAIN ANALYZE
SELECT DISTINCT 
    CONCAT(c.last_name, ' ', c.first_name), 
    SUM(p.amount) OVER (PARTITION BY c.customer_id, f.title)
FROM 
    payment p, 
    rental r, 
    customer c, 
    inventory i, 
    film f
WHERE 
    DATE(p.payment_date) = '2005-07-30' 
    AND p.payment_date = r.rental_date 
    AND r.customer_id = c.customer_id 
    AND i.inventory_id = r.inventory_id;
 ```
   
Узкие места:
- 1. Неявные JOIN (перечисление таблиц через запятую) — может привести к декартову произведению.

- 2. Использование DATE(p.payment_date) — блокирует использование индекса по payment_date.

- 3. Оконная функция с PARTITION BY c.customer_id, f.title — избыточная нагрузка из-за дублирования данных.

- 4. DISTINCT — попытка убрать дубликаты, созданные оконной функцией.

- 5. Отсутствие индексов на ключевых полях (payment_date, rental_id).

Оптимизированный запрос:

```
-- Добавление индексов (если их нет)
CREATE INDEX idx_payment_date ON payment(payment_date);
CREATE INDEX idx_rental_id ON rental(rental_id);

-- Оптимизированный запрос
EXPLAIN ANALYZE
SELECT 
    CONCAT(c.last_name, ' ', c.first_name) AS customer_name,
    SUM(p.amount) AS total_amount
FROM 
    payment p
JOIN rental r ON p.rental_id = r.rental_id
JOIN customer c ON r.customer_id = c.customer_id
JOIN inventory i ON r.inventory_id = i.inventory_id
JOIN film f ON i.film_id = f.film_id
WHERE 
    p.payment_date >= '2005-07-30' 
    AND p.payment_date < '2005-07-31'
GROUP BY 
    c.customer_id, f.film_id;
```

Изменения:

- Явные JOIN с указанием условий.

- Убрана оконная функция — используется GROUP BY.

- Условие по дате через диапазон для использования индекса.

- Убран DISTINCT — группировка устраняет дубликаты.

Результаты оптимизации:

- Сокращение времени выполнения за счет исключения оконной функции и DISTINCT.

- Использование индексов для фильтрации по дате.

- Улучшение читаемости запроса.


`Скриншот исходного запроса и время выполнения:`
![Скриншот-2](https://github.com/Neoju5t/Index/blob/8f587b7e62134bcffdf97ebe3ce55d32fc53b632/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2015.59.29.png)

`Скриншот оптимизированного запроса и время выполнения:`
![Скриншот-3](https://github.com/Neoju5t/Index/blob/8f587b7e62134bcffdf97ebe3ce55d32fc53b632/img/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202025-05-24%20%D0%B2%2015.58.46.png)

---
