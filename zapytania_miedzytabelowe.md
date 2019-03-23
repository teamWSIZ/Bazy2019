
## Przeszukiwanie kilku tabel na raz - przykład
```
select o.orderid as Zamowienie, o.employeeid, o.orderdate, s.shippername,
       c.customername || '(' || c.customerid || ')' as Klient,
       d.quantity as Sztuk
  from orders o, customers c, shippers s, orderdetail d
  where o.customerid = c.customerid and
        o.shipperid = s.shipperid and o.orderid = d.orderid
  limit 20;
```

## Zadania: 

* Znaleźć sumę wszystkich zamówień (w sensie kwoty, $$$),

* Znaleźć sumę zamówień klientów z Polski,

* Znaleźć sumę zamówień per country,

* Znaleźć sumę zamówień w roku 1997

* Wyznaczyć najwięcej zamawiających klientów (w sensie $$$), wypisać pięciu topowych

* Wyznaczyć pięć produktów z których otrzymaliśmy najwięcej zamówień (w sensie $$$)

