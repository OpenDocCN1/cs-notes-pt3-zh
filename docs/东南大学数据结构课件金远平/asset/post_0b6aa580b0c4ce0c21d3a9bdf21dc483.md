
# Example 1.5 **Permutation Generator**

**Problem:** for a set of n ≥ 1 elements, print all possible permutations of it.

# Solution:

look at (a,b,c), the answer is by printing:

+   1. a followed by all permutations of (b,c)
+   2. b followed by all permutations of (a,c)
+   3. c followed by all permutations of (b,a)

```
else {  // a[k:m] has more than one permutation.
    // generate recursively
    for (i=k; i<=m; i++) {
        swap(a[k], a[i]); // interchange a[k] and a[i]
        Permutations(a,k+1,m); // all permutations of a[k+1:m]
        swap(a[k], a[i]); // to return to the original configuration
        // important
    }
}
```

To invoke: Permutation(a,0,n-1)

# Try it with n=3 and a[0:2]=(a,b,c)

((a,b,c),0,2)

((a,b,c),1,2)

((b,a,c),1,2)

((c,b,a),1,2)

((a,b,c),2,2) → a b c

((a,c,b),2,2) → a c b

((b,a,c),2,2) → b a c

((b,c,a),2,2) → b c a

((c,b,a),2,2) → c b a

((c,a,b),2,2) → c a b

# If the original configuration were not returned,

((a,b,c),0,2)
((a,b,c),1,2) → ((a,b,c),2,2) → a b c
((a,c,b),2,2) → a c b
((c,a,b),1,2) → ((c,a,b),2,2) → c a b
((c,b,a),2,2) → c b a
((a,b,c),1,2) repeated !
and the b x x permutations would be lost.

# Exercises: P32-2, P33-14

# 1.7 Performance Analysis and
Measurement

**Definition:** the **Space complexity** of a program is the amount of memory it needs to run to completion. The **Time complexity** of a program is the amount of computer time it needs to run to completion.

+   1. Priori estimates --- Performance analysis
+   2. Posteriori testing--- Performance measurement

# 1.7.1 Performance Analysis

# 1.7.1.1 Space complexity

The space requirement of program P:
S(P)=c+Sₚ(instance characteristics)
We concentrate solely on Sₚ.

# Example 1.10

```
float Rsum (float *a, const int n) //compute ∑_{i=0}^{n-1} a[i] recursively
{
    if (n <=0) return 0;
    else return (Rsum(a,n-1)+a[n-1]);
}
```

The instances are characterized by n, each call requires 4 words (n, a, return value, return address), the depth of recursion is n+1, so

$S_{rsum}(n)=4(n+1)$

# 1.7.1.2 Time complexity

Run time of a program P:
 tₚ(instance characteristics)

A program step is loosely defined as a syntactically or semantically meaningful segment of a program that has an execution time that is independent of instance characteristics.

In P41-43 of the textbook, there is an detailed assignment of step counts to statements in C++.

Our main concern is on how many steps are needed by a program to solve a particular problem instance?

2 ways:

+   (1) count
+   (2) table

# Example 1.12

```
count=0;
float Rsum (float *a, const int n)
{
    count++; // for if
    if (n <=0) {
        count++; // for return
        return 0;
    }
    else {
        count++; // for return
        return (Rsum(a,n-1)+a[n-1]);
    }
}
```

t<sub>Rsum</sub>(0) = 2,
 t<sub>Rsum</sub>(n) = 2+ t<sub>Rsum</sub>(n-1)
    = 2+2+ t<sub>Rsum</sub>(n-2)
    .
    .
    .
    = 2n+ t<sub>Rsum</sub>(0)=2n+2

# Example 1.14 Fibonnaci numbers

```
1 void Fibonnaci (int n)
2 { // compute the Fibonnaci number Fₙ
3   if (n <=1) cout << n<< endl; { // F₀=0 and F₁ =1
4 else { // compute Fₙ
5   int fn; int fnm2=0; int fnm1=1;
6   for (int i=2; i<=n; i++)
7   {
8     fn=fnm1+fnm2;
9     fnm2=fnm1;
10    fnm1=fn;
11  } //end of for
```

```
12    cout <<fn<<endl;
13 } //end of else
14 }
```

Let us use a table to count its total steps.

| Line | s/e | frequency | total steps |
|------|-----|-----------|-------------|
| 1 | 0 | 1 | 0 |
| 2 | 0 | 1 | 0 |
| 3 | 1 (n >1) | 1 | 1 |
| 4 | 0 | 1 | 0 |
| 5 | 2 | 1 | 2 |
| 6 | 1 | n | n |
| 7 | 0 | n-1 | 0 |
| 8 | 1 | n-1 | n-1 |
| 9 | 1 | n-1 | n-1 |
| 10 | 1 | n-1 | n-1 |
| 11 | 0 | n-1 | 0 |
| 12 | 1 | 1 | 1 |
| 13 | 0 | 1 | 0 |
| 14 | 0 | 1 | 0 |

So
for n>1, t_Fibonnci(n)=4n+1,
for n=0 or 1, t_Fibonnci(n) =2

Sometime, the instance characteristics is related with the content of the input data set.

e.g., *BinarySearch*.

Hence:

+   - best-case
+   - worst-case,
+   - average-case.
