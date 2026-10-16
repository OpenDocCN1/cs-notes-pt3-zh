```
int f(int x, int y){
    return x*y;
}
void main(){
    int a=3, b=2,x=9;
    int c;
    c=f(a+b,a+x);
    printf("%d\n", c);
    printf("%d\n", x);
}
程序输出为:
    60
    9
```

内存

|  |  |
|---|---|
| y | 12 |
| x | 5 |
| f 返回值 | 60 |
| c | 60 |
| x | 9 |
| b | 2 |
| a | 3 |
| main |  |