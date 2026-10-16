# 2.2 线性表的存储结构----一元多项式(Cont.)

```
p = p→link ;
break ;
case ‘<‘:
    d = Attch( q→coef, q→exp, d ) ;
    q = q→link ;
    break ;
}
while ( p != NULL )
{
    d = Attch( p→coef, p→exp, d ) ;
    p = p→link ;
}
while ( q !=NULL )
{
    d = Attch( q→coef, q→exp, d ) ;
    q = q→link ;
}
```