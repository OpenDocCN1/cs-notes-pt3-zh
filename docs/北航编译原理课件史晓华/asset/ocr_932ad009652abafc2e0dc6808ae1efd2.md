# <变量>:: = i['<表达式>']

```
PROCEDURE var;                 /*变量*/
    IF sym ≠ 'i' THEN error
    ELSE BEGIN nextsym;
        IF sym = '[' THEN
            BEGIN  nextsym;
                expr;
                IF sym ≠ ']'
                THEN  error
                ELSE  nextsym;
            END
    END
```