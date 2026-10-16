# 4.2.3.2 进程互斥的硬件实现

2. 硬件提供“交换”指令

```
void swap(int &a,&b){
    int temp;
    temp:=*a; *a:=*b; *b:=temp;
};
```

对一组公共变量： int lock (初始=0);

对一个进程空间： int key;

Pi进入： key=1;

do swap(&lock,&key) while (key==1);

Pi离开： lock=0;