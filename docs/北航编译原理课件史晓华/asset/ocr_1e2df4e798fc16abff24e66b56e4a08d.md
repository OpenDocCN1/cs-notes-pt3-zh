# 构造LASTVT(U)的算法

+   1. 若有规则U::=...a或U::=...aV,则a∈LASTVT(U)

+   2. 若有规则U::=...V,且a∈LASTVT(V),则a∈LASTVT(U)

```
设一个栈ST,和一个布尔数组B
PROCEDURE INSERT(U,a)
    IF NOT B[U,a] THEN
        BEGIN
            B[U,a]:=TRUE; 把(U,a)推进ST栈;
        END;
```