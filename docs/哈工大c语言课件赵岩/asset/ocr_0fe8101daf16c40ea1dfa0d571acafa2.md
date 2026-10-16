# 指针的一宗罪-wild pointer

+   - 不初始化。(wild pointer)

# Demo 4: wild pointer

```
1   short *p; /*declare a pointer variable*/
2   printf("%p \n",p);
3   printf("%d",*p) ;
4   *p=5;
```

+   - 声明时强制带等号。