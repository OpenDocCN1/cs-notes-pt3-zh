# 压入、弹出两种操作的 C 函数：

```
压入
bool push( typeofelement x ){
    if ( top > size-1 )
        return false ;
    else {
        stack[ top ] = x ;
        top = top+1 ;
        return true ;
    }
}
```

```
弹出
typeofelement x ;
bool pop ( void ) {
    if (top <=0)
        return false ;
    else {
        top = top-1 ;
        x = stack[ top ] ;
        return true ;
    }
}
```