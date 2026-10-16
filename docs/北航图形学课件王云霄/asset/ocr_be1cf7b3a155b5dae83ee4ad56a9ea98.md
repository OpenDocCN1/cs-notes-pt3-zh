# 3. 2. 2:

设第 i 个 “吊桶” 记录的相应多边形是 A。

```
if Flag_A=FALSE,
then {Flag_A=TRUE,
将A加到表P中, s ← s+1}
else
{Flag_A= FALSE
将P中删除A, s ← s-1 }
```