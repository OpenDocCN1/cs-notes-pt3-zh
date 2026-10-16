```
/* PROGRAM writeprime */
#include "stdio.h"
bool prime( int m ) {
    int j ;
    for ( j = m / 2 ; j >= 2 ; j-- )
        if ( m%j == 0 )
            return false ;
    return true ;
}
int u,v,n;
void main() {
    n=0; u=3; v=u+2;
    while(n<10){
        if ( prime(u)&&prime(v)&&(v-u)==2 ){
            printf("%5d %5d\n", u , v ) ;
            n++;
        }
        u++; v++;
    }
}
```