可以设计实现输入功能的程序片段如下：

```
v=0;
flag=1;
while (flag){
    card_arr[v] = read_card();
    v++;
    printf("please choose 0_end 1_continue :");
    scanf("%d", &flag);
}
```

其中语句 “card_arr[v] = read_card();”调用函数 read_card 函数带回的值是结构体值，直接送入数组成分变量card_arr[v]中