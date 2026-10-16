# 字符串排序-二维数组实现

```
1 char temp[10];
2 char str[][10] = {"Pascal", "Basic", "Fortran", "Java", "Visual C"};
3 
4 if(strcmp(str[j],str[i])<0)
5 {
6     strcpy(temp ,str[i]);
7     strcpy(str[i],str[j]);
8     strcpy(str[j],str[i]);
9 }
```