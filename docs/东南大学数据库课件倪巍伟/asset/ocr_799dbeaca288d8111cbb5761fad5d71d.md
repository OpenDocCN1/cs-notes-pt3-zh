# 范例p118例6-1

设有S（供应商），P（零件），SP（供应关系）三个关系，关系模式如下：

S (SNUM, SNAME, CITY)
P (PNUM, PNAME, WEIGHT, SIZE)
SP (SNUM, PNUM, DEPT, QUAN)

有如下查询

```
Q：
    SELECT SNAME
      FROM S, P, SP
     WHERE S.SNUM = SP.SNUM
       AND SP.PNUM = P.PNUM
       AND S.CITY = ‘NANJING’
       AND P.PNAME = ‘BOLT’
       AND SP.QUAN > 10000
```