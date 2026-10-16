执行move( 0 , a , c , b ):
调用move函数，进入move； n=0，返回。
调用moveone，打印 “a->b”
调用move函数，进入move； n=0，返回。
move函数执行结束，返回。

```
printf( "pleace input n:");
scanf( "%d" , &n );
move ( n , 'a' , 'b' , 'c' )
```

```
move( 2 , a , c , b );
moveone( a , b );
move( 2 , c , b , a )
```

```
move( 1 , a , b , c );
moveone( a , c );
move( 1 , b , c , a )
```

```
move( 0 , a , c , b );
moveone( a , b );
move( 0 , c , b , a );
```

![](bbox=[0.78, 0.06, 0.95, 0.35])