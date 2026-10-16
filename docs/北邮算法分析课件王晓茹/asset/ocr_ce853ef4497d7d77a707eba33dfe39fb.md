```
MERGE(A, p, q, r)
{
1:    n1 = q-p+1;        //length(L)
2:    n2 = r-q;          //length(R)
3:    creat_arrays L[1...n1+1],R[1...n2+1];
4:    for i=1:n1
5:        do L[i] = A[p+i-1];
6:    for j=1:n2
7:        do R[j] = A[q+j];
8:    L[n1+1] = MAX;
9:    R[n2+1] = MAX;
10:   i = 1;
11:   j = 1;
12:   for k = p:r
13:   {
14:       if L[i] <= R[j]
15:       {
16:           A[k] = L[i];
17:           i = i+1;
18:       }
19:       else
20:       {
21:           A[k] = Q[j];
22:           j = j+1;
23:       }
24:   }
}
```

# MERGE(A, p, q, r)