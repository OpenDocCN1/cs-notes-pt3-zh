# Input size

```
Algorithm 1.9 FIRST
Input: A positive integer n and an array A[1..n] with A[j] = j for 1 ≤ j ≤ n.
Output: ∑_{j=1}^n A[j].
1. sum ← 0;
2. for j ← 1 to n
3.   sum ← sum + A[j]
4. end for
5. return sum
```

```
Algorithm 1.10 SECOND
Input: A positive integer n.
Output: ∑_{j=1}^n j.
1. sum ← 0;
2. for j ← 1 to n
3.   sum ← sum + j
4. end for
5. return sum
```

| | Algo 1.9 | Algo 1.10 |
|---|---|---|
| input size | n | □log n□ +1 |
| time | n | n |
| relation | Linear | Exponential |