# Group By statements

```sql
select max(amount)
from payment;

select round(avg(amount), 2)
from payment;

select min(amount)
from payment;

select count(amount) from payment
where amount = 0;

select sum(amount) from payment;

select customer_id, sum(amount)
from payment
group by customer_id;

select customer_id, sum(amount)
from payment
group by customer_id
order by sum(amount) desc;

select staff_id, count(*)
from payment
group by staff_id;

select rating, count(*)
from film
group by rating;

select rental_duration, count(*)
from film
group by rental_duration
order by count(*) desc;

select rating, round(avg(rental_rate),2)
from film
group by rating
order by avg(rental_rate) desc;

select staff_id, count(amount), sum(amount)
from payment
group by staff_id
order by sum(amount) desc;

select rating, round(avg(replacement_cost), 2)
from film
group by rating
order by avg(replacement_cost) desc;

select customer_id, sum(amount)
from payment
group by customer_id
order by sum(amount) desc
limit 5;

select customer_id, sum(amount)
from payment
group by customer_id
having sum(amount) > 200;

select store_id, count(customer_id)
from customer
group by store_id
having count(customer_id) > 300;

select rating, round(avg(rental_rate), 2)
from film
where rating in ('R', 'G', 'PG')
group by rating
having avg(rental_rate) < 3;

select customer_id, count(amount)
from payment
group by customer_id
having count(amount) >= 40
order by count(amount) desc;

select rating, round(avg(rental_duration), 2)
from film
group by rating
having avg(rental_duration) > 5
order by avg(rental_duration) asc;

```