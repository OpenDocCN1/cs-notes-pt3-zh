(5)若定义了一个指针变量使它指向一个字符串，就可以用下标形式引用指针变量所指字符串中的字符。

```
如： char *a="I love China!"; printf("%c",a[5]);
```

(6)用指针变量指向一个格式字符串，可以用它代替printf函数的格式字符串。

```
如： int a; char *format; format="a=%d\n";
则： printf(format,a);相当于printf("a=%d\n",a);
```

(7)若把字符指针指向字符数组，应注意数组的长度。

```
如： char str1[10],*ps=str1; ps[10]='\0'; ✗
```