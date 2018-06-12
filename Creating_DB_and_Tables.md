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