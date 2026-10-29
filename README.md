# Домашнее задание к занятию «SQL. Часть 2»
# Городилов Лев

## Задание 1

```sql
SELECT 
    CONCAT(s.first_name, ' ', s.last_name) AS staff_name,
    ci.city,
    COUNT(c.customer_id) AS customer_count
FROM store st
JOIN staff s ON st.manager_staff_id = s.staff_id
JOIN address a ON st.address_id = a.address_id
JOIN city ci ON a.city_id = ci.city_id
JOIN customer c ON st.store_id = c.store_id
GROUP BY st.store_id, s.first_name, s.last_name, ci.city
HAVING COUNT(c.customer_id) > 300;
```

## Задание 2

```sql
SELECT COUNT(*) AS films_count
FROM film
WHERE length > (SELECT AVG(length) FROM film);
```

## Задание 3

```sql
SELECT 
    DATE_FORMAT(p.payment_date, '%Y-%m') AS payment_month,
    SUM(p.amount) AS total_payment,
    COUNT(r.rental_id) AS rental_count
FROM payment p
JOIN rental r ON p.rental_id = r.rental_id
GROUP BY payment_month
ORDER BY total_payment DESC
LIMIT 1;
```

