# LR(0)和GOTO的构造算法:

```
G'→LR(0), GOTO
Procedure ITEMSETS(G')
begin
    LR(0) := {closure({E'→.E})};
    repeat
        for LR(0)中的每个项目集I和G'的每个符号X do
            if GOTO(I , X)非空,且不属于LR(0)
            then 把GOTO(I , X)放入LR(0)中
    until LR(0)不再增大
end
```