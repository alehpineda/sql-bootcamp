# Extra: Views

```sql
-- Crear un view de un query mas complicado.
create view customer_info as
select first_name, last_name, email, address, phone
from customer
join address
on customer.address_id = address.address_id;

-- Mandar llamar el view
select * from customer_info;

-- Cambiar el nombre de la vista
alter view customer_info rename to customer_data;

-- Eliminar vistas
drop view customer_data;

-- Eliminar vista si existe
drop view if exists customer_data;
```