# # 第14章 继承

```
class Base{
private:
    int i,j;
public:
    void SetIJ(int,int);
    void Getij(int&,int&);
};
```

```
class Derived:Base{
private:
    int k;
public:
    void SetK(int);
    int GetK( );
};
```

类Derived中有三个数据成员和四个函数成员。