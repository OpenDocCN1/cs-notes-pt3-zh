# 7.引用的使用—用引用返回值

```
float t;
float f1(float r)
{ float k; k=3.14*r*r;
    cout<<"f1::k is"<<&k<<endl;
    return(k);}

float& f2(float r)
{ t=3.14*r*r;
    cout<<"f2::t is"<<&t<<endl;
    return(t);
}
float &f3(float r)
{ float f; f=3.14*r*r;
    cout<<"f3::f is"<<&f
    <<endl;
    return(f);
}
```

```
int main()
{ float a=f1(5);
    const float &b=f1(5);
    cout<<"b:"<<&b<<endl;
    cout<<"a="<<a<<","<<"b="
    <<b<<endl;
    float c=f2(5);
    float & d=f2(5);
    cout<<"d:"<<&d<<endl;
    cout<<"c="<<c<<","<<"d="
    <<d<<endl;
    float e=f3(5);
    float & f=f3(5);
    cout<<"e="<<e<<","<<"f="<
    <f<<endl;}
```

f1::k is0x0013FF08
f1::k is0x0013FF08
b:0x0013FF74
a=78.5,b=78.5

f2::t is0x0042DD68
f2::t is0x0042DD68
d:0x0042DD68
c=78.5,d=78.5

f3::f is0x0013FF08
f3::f is0x0013FF08
e=5.88384e-039,f=5.88384e-039