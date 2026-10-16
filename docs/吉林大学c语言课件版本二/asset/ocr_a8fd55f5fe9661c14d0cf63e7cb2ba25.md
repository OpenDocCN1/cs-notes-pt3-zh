```
```c
/* PROGRAM Debruijn2 */
/* 声明部分同前，略 */
void extend(int *m){
(*m)++;
A[*m]=0;
}
void back(int *m){ /* 修正本位函数 */
while(A[*m]==1)
(*m)-- ;
A[*m]=1;
}
```
```

```
```c
void extend(int *m){ /* 延长函数 */
(*m)++;
A[*m]=0;
}
void back(int *m){ /* 回朔 */
while(A[*m]==1)
(*m)-- ;
A[*m]=1;
}
```
```