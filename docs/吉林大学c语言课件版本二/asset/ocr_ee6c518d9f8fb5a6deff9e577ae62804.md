```
#include "stdio.h"
#define nn 10
int n, r;
int a[ nn ], k;
void combination( int s, int j ) {
    int i;                 /* △ */
    for ( i=s; i<=n-j+1; i++ ) {
        a[r-j]=i;           /* r-j不能用s */   /* ◇ */
        if ( j>1 )
            combination( i+1 , j-1 ); /* ☆ */
        else {
            for (k=0;k<r;k++)
                printf("%6d", a[k]);
            printf("\n");
        } /* □ */
    } /* $ */
}
int main (void) {          /* ◎ */
    printf("Enter n,r:");
    scanf("%d%d", &n, &r ); /* ◎ */
    combination( 1,r );      /* ※ */
}
```