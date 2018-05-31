# SQL Statements fundamentals

```sql
select address_id, address from address;

SELECT * FROM actor;

SELECT first_name, last_name, email 
FROM customer;

SELECT DISTINCT release_year FROM film;

SELECT DISTINCT rental_rate FROM film;

SELECT DISTINCT rating FROM film;

SELECT email 
FROM customer
WHERE first_name = 'Jared';

SELECT * 
FROM payment
where amount = 7.99;

SELECT * 
FROM payment
where amount < 5;

SELECT * 
FROM payment
where amount <= 4.99;

SELECT amount, payment_date 
FROM payment
where amount != 4.99;

SELECT amount, payment_date 
FROM payment
where amount = 4.99 or amount = 1.99;

select * from customer
where store_id = 1 
and address_id > 5;

select * from customer
where store_id = 1 
or store_id = 2;

select email
from customer
where first_name = 'Nancy' 
and last_name = 'Thomas';

select description 
from film
where title = 'Outlaw Hanky';

select phone 
from address
where address = '259 Ipoh Drive';

select COUNT(*) 
from payment;

select count(amount)
from payment;

select count(distinct(amount))
from payment;

select *
from customer
limit 5;

select *
from film
limit 1;

select first_name, last_name
from customer
order by first_name asc
limit 5;

select first_name, last_name
from customer
order by first_name desc
limit 5;

select first_name, last_name
from customer
order by last_name desc
limit 5;

select first_name, last_name
from customer
order by first_name asc,
last_name desc
limit 20;

select first_name 
from customer 
order by last_name
limit 5;

select customer_id, amount
from payment
order by amount desc
limit 10;

select film_id, title 
from film 
order by film_id asc
limit 5;

select customer_id, amount 
from payment
where amount between 8 and 9;

select customer_id, amount 
from payment
where amount not between 8 and 9;

select amount, payment_date
from payment
where payment_date between '2007-02-07' and '2007-02-15'
limit 30;

select amount, payment_date
from payment
where payment_date not between '2007-02-07' and '2007-02-15'
limit 100;

select customer_id, rental_id, return_date
from rental
where customer_id 
in (1,2)
order by return_date desc;

select customer_id, rental_id, return_date
from rental
where customer_id 
in (7,13,10)
order by return_date desc;

select * 
from payment
where amount
in (7.99, 8.99);

select first_name, last_name
from customer
where first_name like 'Jen%';

select first_name, last_name
from customer
where first_name like '%y';

select first_name, last_name
from customer
where first_name like '%er%';

select first_name, last_name
from customer
where first_name like '_en%';

select first_name, last_name
from customer
where first_name not like 'Jen%';

select first_name, last_name
from customer
where first_name ilike 'BAR%';

select first_name, last_name
from customer
where first_name ilike 'BaR%';

select first_name, last_name
from customer
where first_name like 'BAR%';

select count(amount) 
from payment 
where amount > 5;

select count(first_name) 
from actor 
where first_name like 'P%';

select count(distinct(district)) 
from address;

select distinct(district) 
from address;

select count(*) 
from film
where rating = 'R' 
and replacement_cost between 5 and 15;

select count(*)
from film
where title like '%Truman%';
```
