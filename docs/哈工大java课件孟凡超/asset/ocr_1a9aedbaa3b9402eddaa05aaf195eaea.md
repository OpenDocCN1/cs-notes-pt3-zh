# 3.2控制流

•在块中和标号配合使用，语法格式为：break 标号；其语义是跳出标号所标记的语句块，继续执行其后的语句。

```
int i, j=0, k=0, h;
label1:for(i=0; i<100; i++, j+=2) {
    switch(i%2) {
        case 1:
            h=1;
            break;
        default:
            h=0;
            break;
    }
    if(i==50)
        break label1;
}
System.out.println("i="+i);
```