# # Creating a Function

Almost exactly like creating a procedure, but you supply a return type

```
```sql
CREATE [OR REPLACE] FUNCTION
function_name
[(parameter1 [mode1] datatype1,
   parameter2 [mode2] datatype2,
   ... )]
RETURN datatype
IS|AS
PL/SQL Block;
```
```