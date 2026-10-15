# 负数

```
double primary()
{ Token t = ts.get();
  switch (t.kind) {
  case '(':        // handle '(' expression ')'
    { double d = expression();
      t = ts.get();
      if (t.kind != ')') error("')' expected");
      return d;
    }
  case '8':        // we use '8' to represent a number
    return t.value;  // return the number's value
  case '-':
    return - primary();
  case '+':
    return primary();
  default:
    error("primary expected");
  }
}
```