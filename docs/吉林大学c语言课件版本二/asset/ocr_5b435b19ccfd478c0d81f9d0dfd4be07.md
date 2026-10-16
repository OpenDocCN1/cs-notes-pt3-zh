```
```c
#define MINNUM -2147483648
#define m 1000
#define n m-1
int a[m] ;
int length ( void ) {
int b[m] , i, j, k ;
b[0] = MINNUM ;
b[1] = a[1] ;
k = 1 ;
for ( i=2 ; i<=n ; i++ )
if ( a[i]>=b[k] ) {
k=k+1 ;
b[k]=a[i]
} else
for ( j=k ; j>0 ; j-- )
if ( ( b[j-1]<=a[i]&& a[i]<b[j] ) )
b[j]=a[i] ;
return k ;
}
```
```