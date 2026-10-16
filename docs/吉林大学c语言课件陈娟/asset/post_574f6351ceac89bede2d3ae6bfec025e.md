
解：
还是分别用试探法和穷举法来解该题。
先考虑环的表示，
对任意n，环上有2^n个0、1。
用一维数组A保存环上的数据。
A的长度nn=2^n。
并且认为A[nn-1]与A[0]相接构成环。

## Debruijn 问题 递归实现穷举法

Debruijn1

输入n

计算2ⁿ =>nn

穷举(0)

结束

枚举(m)

for(i=0;i<=1;i++)

A[m]=i;
枚举(m+1)

m<nn

check(nn-1)

输出

返回

```
int nn;                         // 记录环的长度
int A[ 256 ];                   /* 保存环,限制输入 n 最大为 8 */
bool check( int u );            /* 检查A[0]~A[u]的个n位整数是否不同，略 */
void  out();                    /* 输出A数组，略 */
int power(int w );              /* 求 nn，略 */
void  next( int m ){            /* 枚举 */
    int i;
    if( m < nn )
        for( i=0; i<=1; i++ ){
            A[m] = i;
            next( m+1 );
        }
    else if( check(nn-1) )      // 检验合格
        out();
}
int main(void){                 /* 主程序 */
    int n ;
    printf("\n pleace input n="); scanf( "%d", &n );  /* 输入n<=8 */
    nn=power(n);                /* 求nn */
    next(0);
}
```

## Debruijn 问题 试探法迭代实现

环上一定有n个连续0组成的n位二进制数0。作为初值把n个0放在最前边，从第m=n-1位开始试探。找到一个解输出后，令m=0，使循环终止。算法如图：

![](img/2c9b154d61523ac3dc02daf316966b8e_983_0.png)

# 修正当前位置(*m)

```
def
```

```
A[*m]==1
```

```
(*m)--
```

```
A[*m]=1
```

返回

# 延长(*m)

```
(*m)++
```

```
A[*m]=0
```

返回

```
/* PROGRAM Debruijn2 */    /* 声明部分同前，略 */
void extend(int *m){
    /* 延长函数 */
    (*m)++;
    A[*m]=0;
}

void back(int *m){
    /* 修正本位函数 */
    while(A[*m]==1) (*m)--;    /* 回溯 */
    A[*m]=1;                  /* 修正本位 */
}
```

```
int main(void) {
    int n,i;
    int m;   // m 记录当前处理位置。注意m是局部量，
             // 为了在子程序中修正它，使用指针参数。
    printf("\n please input n=");
    scanf("%%d", &n);  /* 输入n <=8 */
    nn=power(n);                       /* 求nn */
    for ( i=0; i<n; i++ )   A[i]=0;
        m=n-1;                          /* 以上试探初值 */
    while ( m >= n-1 )
        if ( check(m) )
            if ( m == nn-1 ) {   //若A[0]到A[m]正确，且长度够
                out();           // 输出
                m=0 ;            // 退出程序标记
            } else  extend(&m);        /* 延长 */
        else
            back(&m);
}
```

## Debruijn 问题 试探法递归实现

初始状态仍用前 n 个 0。从第 n+1 位开始递归试探。

Debruijn
试探法

输入 n; 计算 nn

for(i=0;i<n;i++)

A[i]=0;

flag=true ;
next(n)

结束

next(m)

flag

结束

m < nn

a[m]=0

check(m)

next(m+1)

a[m]=1

check(m)

next(m+1)

out ;
flag=false

```
/* PROGRAM Debruijn3 */
/* 声明部分同前，略 */
void next( int m ) {
    if ( flag ) {                /* 试探结束 */
        if ( m<nn ) {
            A[m]=0;
            if ( check(m) )
                next(m+1);          /* 延长 */
            A[m]=1;                 /* 修正本位 */
            if ( check(m) )
                next(m+1);          /* 延长 */
        } else {
            out();
            flag=false;
        }
    }
}
```

```
int main(void) {
    printf("\n pleace input n=") ;
    scanf( "%d", &n ) ;        /* 输入n<=8 */
    nn=power(n);               /* 求nn=* */
    for ( i=0; i<n; i++ )
        A[i]=0;                /* 以上试探初值 */
    flag=true;
    next(n);
}
```

## 检验函数 check

为了检验环上已存在哪些n位二进制数，用一个数组 B，保存已检验过的互不相同的n位二进制数。check 的参数u为当前放入数组A中的“0、1”个数。在穷举法中用nn作实在参数对应该u，在试探法中用每步试探时的序列长度m为实在参数对应该u。

# check(u)

```
v=0
```

```
for( i=n-1;
 i<=u;
 i++ )
```

```
A[i-n+1]~A[i]翻译成10进制 => k;
```

```
B中有k
```

```
return false
```

```
B[v]=k;
v++
```

```
u == nn
```

```
for( i= u-n+2;
 i<=u;
 i++ )
```

```
A[i]~A[u]后边补上
n-(u-i+1)个0
翻译成10进制 => k;
```

```
B中有k
```

```
return false
```

```
B[v]=k;
v++
```

```
return true
```

# 结束

```
bool check( int u) {
    int i,j,k;
    int b[256],v;
    v=0 ;
    for ( i=n; i<=u; i++ ) {
        k=trans(i-n+1 , i);        /* A[i-n+1]~A[i]翻译成10进制=>k */
        if test_b( k , b , v )        /* 检验B中有k */
            return false ;
        b[v] = k ;
        v++;
    }
    if ( u==nn ) {
        /* 以下处理A[i]~A[u]+后边n-(u-i+1)个0 */
        for ( i=u-n+2; i<=u; i++ ) {    /* 初始位置是u-n+2而不是u-n+1 */
            k= trans( i , u );          /* 翻译A[i]~A[u]部分 */
            for (j=1;j<=n-(u-i+1);j++)  /* 后边补n-(u-i+1)个0 */
                k = k*2;
            if test_b( k , b , v )      /* 检验B中有k */
                return false ;
            b[v] = k ;
            v++;
        }
    }
    return true;                    /* 检验结果值 */
}
```
