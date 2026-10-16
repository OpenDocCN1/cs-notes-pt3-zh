# 从用户代码开始

```
AB.C

main()
{
    if(!fork()){while(1)printf("A");}
    if(!fork()){while(1)printf("B");}
    wait();
}
```