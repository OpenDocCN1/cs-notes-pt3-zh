# 用管程构造PV操作

```
TYPE
semaphore=MONITOR(init_value)
    VAR c:condition;
        count: integer;
DEFINE P,V;
PROCEDURE P;
    BEGIN
        count:=count-1;
        IF count<0 THEN
            wait(c);
    END;

PROCEDURE V;
    BEGIN
        count:=count+1;
        IF count <=0 THEN
            signal(c);
        END;
    BEGIN
        count:=init_value;
    END;
```