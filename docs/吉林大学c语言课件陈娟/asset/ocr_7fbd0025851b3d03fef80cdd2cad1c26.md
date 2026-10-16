# # 习题7.7

```c
char s[6]="pascal";
```
声明字符数组并赋值“pascal”,但编译时出现数组溢出错误。

```c
char s[]="pascal";
```
声明字符数组并赋值“pascal”

```c
char *s="pascal";
```
声明字符指针并使其指向常量字符串“pascal”

```c
char s[]={'p','a','s','c','a','l','0'};
```
同二

```c
char* s[2]={"pascal","fortran"};
```
声明字符指针数组,并使其分别指向常量字符串“pascal”和“fortran”