
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


## Jakieś rozwiązania
```

select sum(d.quantity * p.price)
from orders o, orderdetail d, products p
where o.orderid = d.orderid and d.productid = p.productid;


select sum(d.quantity * p.price)
from orders o, orderdetail d, products p, customers c
where o.orderid = d.orderid and d.productid = p.productid and c.customerid = o.customerid and
      c.country = 'Poland';

select c.country, round(sum(d.quantity * p.price) / 1e6) as orders_mln
from orders o, orderdetail d, products p, customers c
where o.orderid = d.orderid and d.productid = p.productid and c.customerid = o.customerid
group by country
order by orders_mln desc;


SELECT
  ROUND( 10.812, 0 );
```
