# 例:指针常量

```
```cpp
int a[10];
int * const p=a;
int b[6];
p=b; // 错误
*p=6; // 正确
*(p+6)=6; // 正确
*p++ = 7; // 错误
const int c=0;
int *const q=&c; // 错误
```
```

# 例:常量指针

```
```cpp
const int a=78;
const int b=28;
int c=18;
const int *pi=&a;
pi=&b; //ok
*pi=68; //error
pi=&c; //ok
*pi=88; //error
c=98; //ok
```
```

错误 (a本身不能被修改就不允许外界提供修改的漏洞)