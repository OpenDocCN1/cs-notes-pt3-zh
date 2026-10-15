# Translating Conditional Branches

```
if ( test-expr )
    then-statement
else
    else-statement
```

```
t = test-expr ;
if ( t )
    goto true ;
else-statement
goto done

true:
    then-statement

done:
```