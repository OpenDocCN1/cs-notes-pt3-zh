```
(1) char *str="I am a teacher";
    printf ( "%s", str);
    // 正确，打印： I am a teacher
```

```
(2) char *str="I am a teacher";
    str = str+5;
    printf ( "%s", str);
    // 正确，打印： a teacher
```

```
(3) char *str= "x=%d y=%f\n";
    printf (str , x , y );
    // 正确，相当于: printf ("x=%d y=%f\n" , x , y );
```