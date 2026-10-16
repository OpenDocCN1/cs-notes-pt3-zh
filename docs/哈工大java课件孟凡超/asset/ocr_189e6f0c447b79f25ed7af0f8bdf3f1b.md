# 3.2 控制流

# break与continue语句

break语句： break语句可用于三类语句中，一类是switch语句中，一类是for、while及do等循环语句中，还有一类是块语句中。

+   在switch语句及循环语句中，break的语义是跳过本块中余下的所有语句，转到块尾，执行其后的语句。

```
int i,j;
for(i=0;i<10;i++){
    for(j=0;j<8;j++){
        if(i==5&&j==5)
            break;
    }
    System.out.println("i="+i+";j="+j);
}
```