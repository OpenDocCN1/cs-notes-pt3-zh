```
```sql
PROCEDURE enter(VAR instance:one_)
BEGIN
    P(instance.mutex)
END

PROCEDURE leave(VAR instance:one_)
BEGIN
    V(instance.mutex)
END;
```
```