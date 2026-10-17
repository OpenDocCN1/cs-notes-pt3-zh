```
System.out.println(" Array c*d");
for(i=0;i<3; i++) {
    for(j=0;j<3;j++) {
        e[i][j]=0;
        for ( k = 0 ; k < 3 ; k ++ )
        e[i][j]=e[i][j]+c[i][k]*d[k][j] ;
        System.out.print(e[i][j]+"\t"); }
    System.out.println(); }
}
}
```