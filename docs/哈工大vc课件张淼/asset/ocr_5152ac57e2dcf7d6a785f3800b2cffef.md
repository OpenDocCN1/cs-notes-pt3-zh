# <<和>>的重载

为了能用>>和<<对自定义类的对象进行输入输出操作，就需要对自定义的类重载<<和>>。

```
class A
{int x,y;
public:
    friend ostream& operator <<(ostream & out,const A &a)
}
```