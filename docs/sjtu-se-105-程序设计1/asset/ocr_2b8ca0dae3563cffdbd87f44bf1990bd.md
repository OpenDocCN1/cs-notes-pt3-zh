# 增加输入提示符和输出指示符

```
double val = 0;
cout << "> ";                         // print prompt
while (cin) {
    Token t = ts.get();
    if (t.kind == 'q') break;              // check for “quit”
    if (t.kind == ';')
        cout << "=" << val << "\n> ";    // print “= result” and prompt
    else
        ts.putback(t);
    val = expression();                    // read and evaluate expression
}
```

```
> 2+3; 5*7; 2+9;  //the program doesn’t see input before you hit “enter/return”
= 5
> = 35
> = 11
>
```