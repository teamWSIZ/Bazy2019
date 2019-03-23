```
set search_path to xxx;


select o.orderid, c.customername, e.lastname || ' '|| e.firstname, o.orderdate, s.shippername
from orders o, customers c, shippers s, employees e
where o.customerid = c.customerid and
      o.shipperid = s.shipperid and
      o.employeeid = e.employeeid;


--wyciągnąć sumę wszystkich zamówień...
--w 1997 r, 2015 r

select sum(d.quantity * p.price)
from orders o, orderdetail d, products p
where o.orderid = d.orderid and d.productid = p.productid;


select avg(d.quantity), count(d.orderid) from orderdetail d;
select avg(p.price) from products p;


select round(sum(d.quantity * p.price) / 1e6) as suma_mln
from orders o, orderdetail d, products p
where o.orderid = d.orderid and d.productid = p.productid;

--- chcemy rozpiskę sprzedarzy per kraj odbiorcy

select c.country, round(sum(d.quantity * p.price) / 1e6) as suma_mln
from orders o, orderdetail d, products p, customers c
where o.orderid = d.orderid and
      d.productid = p.productid and
      o.customerid = c.customerid
group by c.country
order by suma_mln desc
;

--- chcemy znaleźć sumę sprzedaży per rok
select extract('year' from current_timestamp);

select extract('year' from o.orderdate) as year,
       round(sum(d.quantity * p.price) / 1e6) as suma_mln
from orders o, orderdetail d, products p
where o.orderid = d.orderid and
    d.productid = p.productid
group by year
order by suma_mln desc
;

-- chcemy średnią sumę sprzedaży per miesiąc (po wszystkich latach)
select extract('month' from o.orderdate) as month,
       round(sum(d.quantity * p.price) / count(*)) as suma, count(*) as items_in_month
from orders o, orderdetail d, products p
where o.orderid = d.orderid and
    d.productid = p.productid
group by month
order by suma desc
;

```