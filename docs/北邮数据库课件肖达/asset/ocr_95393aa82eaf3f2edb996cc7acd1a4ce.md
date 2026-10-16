+   - Product(maker,model, type)
+   - Laptop(model, speed, ram, hd, screen, price)

查询所有这样的制造商：对于制造商B生产的笔记本所含的内存容量，该制造商所生产的笔记本中都有。

思路：寻找这样的制造商x：不存在这样的内存容量y，制造商B生产的笔记本含有容量y，而制造商x生产的笔记本不含有容量y。

```
select DISTINCT x.maker
from Product x
where not exists
    (select *
    from Laptop y
    where 'B' in
        (select P1.maker
        from Product P1, Laptop L1
        where P1.model=L1.model and L1.ram=y.ram) and
        x.maker not in
        (select P2.maker
        from Product P2, Laptop L2
        where P2.model=L2.model and L2.ram=y.ram));
```