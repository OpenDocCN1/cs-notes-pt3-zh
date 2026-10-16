# 指针的输出

指针输出操作有一个例外：当输出字符指针（char *）时，输出的不是指针值，而是该指针所指向的字符串。

```
char str[]="ABCD";
char *p=str;
cout<<p; //输出： ABCD
cout<<*p; //输出： A
```