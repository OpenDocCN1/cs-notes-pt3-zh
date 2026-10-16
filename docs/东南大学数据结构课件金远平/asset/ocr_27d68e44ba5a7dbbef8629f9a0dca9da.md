```
1 void MatrixDigraph::AllLengths (const int n)
2 { //length[n][n] is the adjacency matrix of G with n vertices.
3   //a[i][j] is the length of shortest path from i to j
4   for (int i=0; i<n; i++)
5     for (int j=0; j<n; j++)
6       a[i][j] = length[i][j]; // copy length into a
7   for ( int k=0; k<n; k++) // for a path with highest index k
8     for (i=0; i<n; i++)   //for all pairs
9       for (j=0; j<n; j++)
10        if (a[i][k]+a[k][j]<a[i][j]) a[i][j]=a[i][k]+a[k][j];
11 }
```

The computation is done in place using a, because A^k[i][k]= A^{k-1}[i][k] and A^k[k][j]= A^{k-1}[k][j].