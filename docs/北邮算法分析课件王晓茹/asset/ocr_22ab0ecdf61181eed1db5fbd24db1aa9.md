# § 3 Compare the Algorithms

【Example】 Given (possibly negative) integers A₁, A₂, ..., A_N, find the maximum value of Σ_{k=i}^j A_k.

# Algorithm 1

```
int MaxSubsequenceSum ( const int A[], int N )
{
    int ThisSum, MaxSum, i, j, k;
    MaxSum = 0; /* initialize the maximum sum */
    for( i = 0; i < N; i++ ) /* start from A[ i ] */
        for( j = i; j < N; j++ ) { /* end at A[ j ] */
            ThisSum = 0;
            for( k = i; k <= j; k++ )
                ThisSum += A[ k ]; /* sum A[ i ] to A[ j ] */
            if ( ThisSum > MaxSum )
                MaxSum = ThisSum; /* update the max sum */
        } /* end for-j and for-i */
    return MaxSum;
}
T(N) = O(N³)
```

Detailed analysis is your first homework.