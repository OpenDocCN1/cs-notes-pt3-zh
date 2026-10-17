# Declaring Variables with the `%TYPE` Attribute

Examples

```
DECLARE
  sname       Sailors.sname%TYPE;
  fav_boat    VARCHAR2(30);
  my_fav_boat fav_boat%TYPE := 'Pinta';
  ...
```

Accessing column sname in table Sailors

Accessing another variable