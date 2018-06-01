# Joins

```sql

select payment_id
as my_payments_column
from payment;

select customer_id, sum(amount) as total_spent
from payment
group by customer_id;

select
customer.customer_id,
first_name,
last_name,
email,
amount,
payment_date
from customer
inner join payment
on payment.customer_id = customer.customer_id
order by customer.customer_id;

select
customer.customer_id,
first_name,
last_name,
email,
amount,
payment_date
from customer
inner join payment
on payment.customer_id = customer.customer_id
order by first_name;

select
customer.customer_id,
first_name,
last_name,
email,
amount,
payment_date
from customer
inner join payment
on payment.customer_id = customer.customer_id
where customer.customer_id = 2;

select
customer.customer_id,
first_name,
last_name,
email,
amount,
payment_date
from customer
inner join payment
on payment.customer_id = customer.customer_id
where first_name like 'A%';

select payment_id, amount, first_name, last_name
from payment
inner join staff on payment.staff_id = staff.staff_id;

select title, count(title) as copies_at_store_1
from inventory
inner join film
on inventory.film_id = film.film_id
where store_id = 1
group by title
order by title;

select title, count(title) as copies_at_store_1
from inventory
inner join film
on inventory.film_id = film.film_id
where store_id = 1
group by title
order by copies_at_store_1 desc;

select title, language.name as movie_language
from film
inner join language on language.language_id = film.language_id;

select title, lan.name as movie_language
from film
inner join language as lan
on lan.language_id = film.language_id;

select title, name as movie_language
from film
join language as lan
on lan.language_id = film.language_id;


```