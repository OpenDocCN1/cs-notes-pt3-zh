```
(8) char *str , str0[20];
str=str0;
scanf ( “%s”,str);
// 正确，输入字符串数据从str0[0]开始存放
```

```
(9) char *str , str0[20];
str=str0+5;
scanf ( “%s”,str);
// 正确，输入数据将从str0[5]开始存放
```

```
(10) char str[20]= “I am a teacher”;
printf ( “%s”,str);
// 正确，打印： I am a teacher
```