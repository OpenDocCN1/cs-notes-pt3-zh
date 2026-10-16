# 显示实例化函数模板

```
template <class T1, class T2, class T3 >
T1 sum(T2 a,T3 b)
{
 ......
}
```

```
int i;long lng;
Sum<long>(i,lng);
```

```
int i;long lng;
Sum<long,int,long>(i,lng);
```