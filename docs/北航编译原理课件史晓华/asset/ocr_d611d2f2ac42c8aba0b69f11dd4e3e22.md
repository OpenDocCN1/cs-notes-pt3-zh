# 具体方法如下：

```
设一个栈S和一个二维布尔数组F
F[U,b]=TRUE   iff b∈FIRSTVT(U)

PROCEDURE  INSERT(U,b)
    IF NOT F[U,b] THEN
        BEGIN
            F[U,b]:=TRUE;
            把(U,b)推进S栈   /* b∈FIRSTVT(U) */
        END
BEGIN {main}
    FOR 每个非终结符号U和终结符b DO
        F[U,b]:=FALSE;
    FOR 每个形如U::=b...或U::=Vb... 的规则 DO
        INSERT(U,b);
```