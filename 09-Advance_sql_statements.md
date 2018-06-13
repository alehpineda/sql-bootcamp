# Advance SQL Statements

```sql
select extract(day from payment_date)
from payment
limit 10;

select customer_id, extract(day from payment_date) as day
from payment
limit 10;

select sum(amount) as total, extract(month from payment_date) as month
from payment
group by month
order by total desc
limit 1;

select customer_id + rental_id as new_id
from payment
limit 5;

select customer_id - rental_id as new_id
from payment
limit 5;

select customer_id * rental_id as new_id
from payment
limit 5;

select customer_id / rental_id as new_id
from payment
limit 5;

select round(avg(amount), 2)
from payment;

select first_name || ' ' || last_name as nombre_completo
from customer
limit 10;

select first_name, char_length(first_name)
from customer
limit 10;

select first_name, upper(first_name)
from customer
limit 10;

select first_name, lower(first_name)
from customer
limit 10;

select film_id, title, rental_rate
from film
where rental_rate > (
    select avg(rental_rate)
    from film);

select inventory.film_id
from rental
inner join inventory
on inventory.inventory_id = rental.inventory_id
where return_date
between '2005-05-29' and '2005-05-30'
order by inventory.inventory_id asc
limit 10;

select film_id, title
from film
where film_id in (
    select inventory.film_id
    from rental
    inner join inventory
    on inventory.inventory_id = rental.inventory_id
    where return_date
    between '2005-05-29' and '2005-05-30'
    order by inventory.inventory_id asc);

select a.customer_id, a.first_name, a.last_name, b.customer_id, b.first_name, b.last_name
from customer as a, customer as b
where a.first_name = b.last_name;

select a.customer_id, a.first_name, a.last_name, b.customer_id, b.first_name, b.last_name
from customer as a
join customer as b
on a.first_name = b.last_name;

select a.customer_id, a.first_name, a.last_name, b.customer_id, b.first_name, b.last_name
from customer as a
join customer as b
on a.first_name = b.last_name
order by b.customer_id;


```