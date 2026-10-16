# 4.2.3.2 进程互斥的硬件实现

+   1. 硬件提供“测试并建立”指令

```
int test_and_set(int &target){
    int temp;
    temp=target;
    *target=1;
    return temp;
}.
```

对一组公共变量，int lock;（初始=0）;

Pi进入： While test_and_set(&lock);

Pi离开： lock=0;

满足互斥性，进展性，不满足有限等待性。