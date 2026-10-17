# # 重载自增运算符

# ## 例

```
class Increase
{ int value;
public :
Increase (int v=0 ) { value= v;}
Increase operator ++ ();    //重载前置++
Increase   operator ++ ( int ); //重载后置++
};
```

```
Increase I1(1), I2 ;
++I1;
I2 = ++I1;
I2 = ++++ I1;//I1结果如
```

```
Increase Increase :: operator ++ ()
{
++value ;
return *this;
}
```

> > 调用复制构造返回对象？