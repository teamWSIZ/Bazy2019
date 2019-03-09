
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