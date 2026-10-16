# 指针的三宗罪-指针越界

+   - 多发生于字符串或数组的越界。

Demo 5: Out of bound 1

```
int age[3] = {28,30,33};
int *p = &age[0];
int index ;
scanf("%d",&index);
*(p+index) = 40;
```