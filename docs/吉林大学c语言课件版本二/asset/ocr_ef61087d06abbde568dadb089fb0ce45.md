```
bool iinp( int ii,int u,int v ) {
    int j;
    for ( j=u; j<=v; j++ )
        if ( ii==p[j] )
            return true;
    return false ;
}
void printp( int e,int f ) {
    int j;
    for (j=e; j<=f; j++)
        printf("%4d", p[j] );
    printf("\n");
}
```