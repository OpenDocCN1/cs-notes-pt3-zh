# 原子A的推理算法TorF(A)如下：

```
TorF(A)
i=0;
while (i<n)    // n是此Horn逻辑程序内子句的个数
{
    if（第i条规则的头部=A）  //用第i条规则考察A
    {
        if（第i条规则的体是空的）then return 1;
                                      // A是事实
        else if（TorF(A₁)=...=TorF(Aₘ)=1）
                 //A₁... Aₘ是第i条规则体内的所有原子
                 then return 1;  //由规则推出原子A的正确
    }
    i=i+1;  //第i条规则体内并非所有原子正确，从而需要考察别的规则
}
return 0;  //考察了所有的规则，都不能推出A
}
```