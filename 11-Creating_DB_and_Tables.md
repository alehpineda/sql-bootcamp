# Creando Bases de datos y Tablas

## Crear una tabla en una nueva db

```sql
create table account(
user_id serial primary key,
username varchar(50) unique not null,
password varchar(50) not null,
email varchar(335) unique not null,
created_on timestamp not null,
last_login timestamp

);

create table role(
role_id serial primary key,
role_name varchar(255) unique not null

);

create table account_role(
user_id integer not null,
role_id integer not null,
grant_date timestamp without time zone,
primary key (user_id, role_id),
constraint account_role_role_id_fkey foreign key (role_id)
    references role(role_id) match simple
    on update no action
    on delete no action,
constraint account_role_user_id_fkey foreign key (user_id)
    references account(user_id) match simple
    on update no action
    on delete no action
);
```

### Crear tabla ejercicios

```sql
create table leads(
-- first name
first_name varchar(100) not null,
-- last name
last_name varchar(100) not null,
-- email
email varchar(335) unique not null,
-- sign-up date
sign_up_date timestamp not null,
-- number of minutes on the store
time_in_store time not null,
-- id tracker
id_tracker serial primary key

);

create table leads_solution(
user_id serial primary key,
first_name varchar(50) not null,
last_name varchar(50) not null,
email varchar(355) unique not null,
minutes integer not null,
sign_up_ts timestamp not null
);

```

### Comando insert

```sql
create table link(
ID serial primary key,
url varchar(255) not null,
name varchar(255) not null,
description varchar(255),
rel varchar(50)
);

insert into link(url, name)
values
('google.com', 'Google');

insert into link(url, name)
values
('yahoo.com', 'Yahoo');

insert into link(url, name)
values
('bing.com', 'Bing'),
('amazon.com', 'Amazon');

-- crear copia de la tabla
create table link_copy(like link);

-- copiar valores de una tabla a otra
insert into link_copy
select * from link
where name like 'Bing'

insert into link (url, name)
values
('aol.com','AOL'),
('gamespot.com', 'GameSpot');

insert into link_copy
select * from link;

```

### Comando UPDATE

```sql
-- Update general
update link
set description = 'Descripcion vacia';

-- Update con where
update link
set description = 'Nombre inicia con A'
where name like 'A%';

-- Update de tabla A en B
update link
set description = name;

-- Update con returning
update link
set description = 'Nueva descripcion'
where id = 3
returning id, url, name, description;

```

### Comando DELETE

```sql
-- Delete con where
delete from link
where name like 'G%';

-- Delete con returning
delete from link
where name = 'AOL'
returning *;

```

### ALTER TABLE

```sql
-- Tirar tabla si existe
drop table if exists link;

-- Creamos nueva tabla
create table link(
    link_id serial primary key,
    title varchar(512) not null,
    url varchar(1024) not null unique
);

-- Agregar nueva columna
alter table link add column active boolean;

-- Eliminar columna
alter table link drop column active;

-- cambiar nombre de columna
alter table link rename column title to new_title_name;

-- cambiar nombre de la tabla
alter table link rename to url_table

```

### DROP Table

```sql
-- crear tabla
create table test_two(
    test_id serial primary key
);

-- ver si existe
select * from test_two;

-- tirar tabla
drop table test_two;

-- tirar tabla si existe
drop table if exists test_two;

-- tirar tabla en cascada (elimina todas las dependencias)
drop table if exists test_two cascade;

-- tirar tabla con restriccion
drop table if exists test_two restrict;
```

### Check Constraint

```sql
-- Nueva tabla
create table new_users(
    id serial primary key,
    first_name varchar(50),
    last_name varchar(50),
    birth_date date
        check(birth_date > '1900-01-01'),
    join_date date
        check(join_date > join_date),
    salary integer
        check(salary>0)
);

-- Agregamos valores que violan el check
insert into new_users(first_name, birth_date, join_date, salary)
values ('Joe', '1980-02-02', '1990-04-04', -10);

-- Constraint con nombre
create table check_test(
    sales integer
        constraint positive_sales
            check(sales>0)
);

-- Agregamos un valor que viola el check
insert into check_test(sales)
values(-12);
```

### NOT NULL Constraint

```sql
-- Crear tabla
create table learn_null(
    first_name varchar(50),
    sales integer not null
);

-- Agregamos valores que violan el check
insert into learn_null(first_name)
values('Juan');

-- Agregamos valores que pasan el check
insert into learn_null(first_name, sales)
values('Juan', '123');
```

### UNIQUE Constraint

```sql
-- Crear tabla con constraint unique
create table people(
    id serial primary key,
    first_name varchar(50),
    email varchar(100) unique
);

-- Agregamos valores
insert into people(id, first_name, email)
values('1', 'Joe', 'joe@joe.com')
-- pasa

-- Agregamos valores
insert into people(id, first_name, email)
values('2', 'Joseph', 'joe@joe.com')
-- viola el constraint

```