```
SELECT  A1
FROM R1'
WHERE R1'.A3 IN
(SELECT A4
FROM  R2
WHERE R2.A5 比较符 R1.A1)
```

看作临时表R1'

将R1'的每个元组逐个代入，检查限制条件是否满足，以减少需检查的上层查询所涉及表的元组数目！

注意：采用代入法时，尽可能作“部分选择”！