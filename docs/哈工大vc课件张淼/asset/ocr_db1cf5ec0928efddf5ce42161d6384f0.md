# 二义性问题举例

```
class B
{public:
    int b;
}
class B1 : public B
{private:
    int b1;
}
class B2 : public B
{private:
    int b2;
};
```

```
class C : public B1,public B2
{public:
    int f();
private:
    int d;
}
```

![](bbox=[0.62, 0.58, 0.92, 0.82])