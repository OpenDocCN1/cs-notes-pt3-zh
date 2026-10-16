# 第九章. 异常处理

```
void f()
{ sock a;
    a=sock("10.100.21.61",5670);
    send(a,"Hello!");
}
```

```
int f()
{ sock a;
    a=sock("10.100.21.61",5670);
    if(a<0){
        cout<<"不能获得网络连接"<<endl;
        return(-1);
    }
    send(a,"Hello!");
}
```

```
main()
{if(f() == -1) cout<<"失败！";}
```