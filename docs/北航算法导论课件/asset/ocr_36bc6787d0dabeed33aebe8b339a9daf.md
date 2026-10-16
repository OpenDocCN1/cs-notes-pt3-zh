# 2.1 Insertion sort

![](bbox=[0.1, 0.24, 0.6, 0.48])

![](bbox=[0.75, 0.1, 0.95, 0.45])

```
INSERTION-SORT(A)
1   for(j = 2; j <= length[A]; j++) // loop header
2   {      key = A[j]
3       // Insert A[j] into the sorted sequence A[1 .. j-1]
4       i <- j-1
5       while(i > 0 && A[i] > key)
6       {      A[i+1] = A[i]
7           i = i-1
8       }
9       A[i+1] = key
10  }   // loop body below
```

Is the algorithm correct?

![](bbox=[0.68, 0.55, 0.88, 0.78])

![](bbox=[0.85, 0.77, 0.95, 0.92])