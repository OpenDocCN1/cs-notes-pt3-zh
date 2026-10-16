# 数组实现-颠倒字符串

reverse a string

```
char a[200] = "abcde";
int len = strlen(a);
char temp;
int i ;
for(i = 0; i<len/2; i++){
    temp = a[i];
    a[i] = a[len-1-i];
    a[len-1-i] = temp;
}
printf("%s\n",a);
```