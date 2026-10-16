# （2）用指针变量来实现对字符串的访问

# 例8.8 将一已知字符串第n个字符开始的剩余字符复制到另一字符串中。

```
main()
{int i,n;
char a[]="computer";
char b[10],*p,*q;

p=a;
q=b;
scanf("%d",&n);
if (strlen(a)>=n) p+=n-1;
/*指针指到要复制的第一个字符 */
```