# 执行主程序：

+   1、输出提示信息；
+   2、要求输入金片个数 n，设输入 “3”；
+   3、调用move函数：进入move； n=3>0，参数替换后，实际

```
printf( “pleace input n:”);
scanf( “%d” , &n );
move ( n , 'a' , 'b' , 'c' )
```

```
move( 2 , a , c , b );
moveone( a , b );
move( 2 , c , b , a )
```