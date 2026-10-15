```
double expression(Token_stream& ts){
    double left = term(ts);
    Token t =ts.get();
    //...
}
```

```
double primary(Token_stream& ts){
    Token t = ts.get();
    switch(t.kind){
    case '(' :
        double d = expression(ts);
        //...
        //...
    }
}
```

```
double term(Token_stream& ts){
    double left = primary(ts);
    Token t = ts.get();
    //...
    case '/' :
        double d = primary(ts);
        //...
    //...
}
```

当函数被调用时，语言实现会设置一块内存空间，用于存放包含所有参数和局部变量副本的数据结构