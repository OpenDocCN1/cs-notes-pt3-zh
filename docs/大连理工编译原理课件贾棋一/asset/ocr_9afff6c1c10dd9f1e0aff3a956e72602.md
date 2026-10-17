# 总结

# LL(1)文法的自上而下分析及FIRST函数据理解

S→A|B　　aaaaa, bbbbc

A→aA|ε　　aaaaa, aa,

B→bB|c　　bbbc, bbc

```
procedure match(t)
{
    if 当前输入符号 = t then 取
    下一个符号作为当前输入符号
    else 报错。
}
procedure A
{
    if 当前符号='a' then
        { match(a); 调用A; }
    else return;
}
```

> 当非终结符的产生式有多种选择，即意味着分析过程有不同的展开方式。而我们只能根据当前输入符号来决定采用哪种展开方式（选择），这样就有了 FIRST（ ）函数。

```
procedure B
{
    if 当前符号='b' then
        { match(b); 调用B; }
    else if 当前符号='c' then return;
    else 报错。
}
procedure S
{
    switch 当前符号
    case 'a': 调用 A;
    case 'b':
    case 'c': 调用 B;
}
```