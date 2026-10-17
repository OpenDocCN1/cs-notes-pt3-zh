# 4.8 Block Structure

+   - **block: `{.....}`**

+   - variable can be declared in a block (follow the left brace),,\n  the scope of the variable is the block and remain in\n  existence until matching the right brace.

```
if(n>0) {\n    int i;        /*declare a new i */\n    for (i=0;i<n; i++)\n    ...\n}
```

the scope of “i”

the variable in inner scope will hide variables in outer scope of the same name.

```
int x,y;\nf(double x)\n{  double y;\n   ...\n   x=y+1;\n   ...\n}\ng()\n...
```

inner first