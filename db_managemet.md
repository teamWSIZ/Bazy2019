
## Tworzenie usera i bazy (z usera postgres)
Założenie: jesteśmy zalogowani userem `postgres` na bazę `postgres`.


```
CREATE USER student WITH PASSWORD 'wsiz#1234';
CREATE DATABASE student;
GRANT ALL PRIVILEGES ON DATABASE student TO student;
```

## Tworzenie u używanie schematu
```
create schema pm;
set search_path to pm;
```
## Tworzenie tabeli
```
create table tt(
  id serial,
  t text
);
```

### dopisywanie danych
select * from tt;

insert into tt(t) values ('Abra');
insert into tt(t) values ('Kadabra');
insert into tt(t) values ('Hokus');
insert into tt(t) values ('Pokus');

### tworzenie bazy customers z w3schools

create table customers
(
  customerid SERIAL,
  customername text,
  contactname text,
  address text,
  city text,
  postalcode text,
  country text
);


