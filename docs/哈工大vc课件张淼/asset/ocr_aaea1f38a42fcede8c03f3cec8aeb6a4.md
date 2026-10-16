```
class A
{ int x;
public:
    A(){x=0;}
    A(int i){x=i;}
};
```

```
class B:public A
{ int y;
public:
    B(){y=0;}
    B(int i){y=i;}
    B(int i,int j):A(i)
    {y=j;} };
```

```
B b;    //A::A(),B::B()
B b2(1);//A::A(),B::B(int)
B b3(1,2);//A::A(int),B::B(int,int)
```