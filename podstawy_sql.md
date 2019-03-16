## Podstawy

https://www.w3schools.com/sql/


## Zapytania wyszukujące

`SELECT * FROM Customers where Country like '%ce';`

## Zadania: 

* Znaleźć liczbę klientów z niemiec i z francji (odp: `SELECT count(*) FROM Customers where Country='France'`)

* Ilu jest klientów z 'Buenos Aires' (odp: `SELECT * FROM Customers where City='Buenos Aires'`)

* Znaleźć wszystkich pracowników (Employees) urodzonych po 1 Stycznia 1965
(odp: `SELECT * FROM Employees where BirthDate > '1/1/1968';`)
lub: `SELECT * FROM Employees where BirthDate > '1950-01-20';`

* Znaleźć pracowników w których opisie (Notes) jest słowo 'fluent'
(odp: `SELECT * FROM Employees where Notes like '%fluent%';`)

* Znaleźć wszystkie zamówienia klienta o numerze 80 (w tabeli 'Orders')

* Znaleźć ostatnie 20 zamówień klienta o numerze 80:
`select * from orders where customerid=80 order by orderdate desc limit 20;`


 
* Znaleźć zamówienia po 1 lipca 1996:
(odp: `SELECT * FROM orders where orderdate > '1/7/1996';`)

* Wypisać klientów sortując ich po krajach i miastach, 
(odp `SELECT * FROM Customers order by Country, City;`)



* Wypisać ile klientów mamy z każdego z krajów
`select country, count(*) from customers group by country order by country;`

*  wypisać tabelę pokazującą ile mamy klientów z każdego z krajów; 
Dodatkowo: 
    - posortować po liczbie klientów
    - wypisać tylko 10 'najlepszych' krajów
     
`select country, count(*) cnt from customers group by country order by cnt desc limit 10;`
(uwaga: `cnt` to jest alias do `count(*)`; można go używać zamiennie)


--zadanie: sprawdzić którzy klienci kupili za nawiększe kwoty



Łączenie z VPN

http://bit.do/wsiz-vpn-tutorial

