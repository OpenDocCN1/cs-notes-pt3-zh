
In general, for a Radix-ℛ sort, r bins are needed.

# Assume:

+   (1) records R₁, R₂, …, Rₙ and their keys are decomposed using a radix of r, each key have d digits in the range of [0, r-1].
+   
+   (2) records have a link field.
+   
+   (3) for each bin i, 0≤ i <r

![](img/15e8d7d94d8ddf02cb6839870195a31e_649_0.png)

```
template <class T>
int RadixSort(T*a, int*link, const int d, const int r, const int n)
{ // Sort a[1:n] using a d-digit radix-r sort. digit(e, i, r) returns
// the ith radix-r digit (from the left, the first is the 0th digit)
// of e’s key. Each digit is in the range of [0, r).
    int e[r], f[r]; // queue end and front pointers

// create initial chain of records starting at first
if (n==0) return 0; int first=1;
for (int i=1; i<n; i++) link[i]=i+1; // linked into a chain
link[n]=0;

for (i=d-1; i>=0; i--)
{ // sort on digit i
    fill(f, f+r, 0); // initialize bins to empty queues
    for (int current=first; current; current=link[current])
    { // put records into queues
```

```
int k=digit(a[current], i, r);
if (f[k]==0) f[k]=current;
else link[e[k]]=current;
e[k]=current;
}
for (int j=0; !f[j] ; j++); // find first nonempty queue
first=f[j]; int last=e[j];
for (int k=j+1; k<r; k++) // concatenate remaining queues
    if (f[k]) {
        link[last]=f[k]; last=e[k];
    }
    link[last]=0;
}
return first;
}
```

# Analysis of RadixSort:

d passes over the data, each taking O(n+r). Hence the total time is O(d(n+r)).

d will depend on r and the largest key.

# Example 7.8: sort 10 numbers in the range [0,999],

r=10, hence d=3.

![](img/15e8d7d94d8ddf02cb6839870195a31e_652_0.png)

(a) Initial input

# (b) First pass

e[0] e[1] e[2] e[3] e[4] e[5] e[6] e[7] e[8] e[9]

f[0] f[1] f[2] f[3] f[4] f[5] f[6] f[7] f[8] f[9]

271 93 33 984 55 306 208 179 859 9

![](img/15e8d7d94d8ddf02cb6839870195a31e_655_0.png)

# (d) third pass

# Exercises: P422-1, 3, 5

# 7.9 Summary of Internal Sorting

The behavior of Radix Sort depends on the size of keys and the choice of r.

The following summarizes the other 4 methods we have studied:

| Method | Worst | Average | Working Storage |
|---|---|---|---|
| Insertion Sort | n² | n² | O(1) |
| Heap Sort | n log n | n log n | O(1) |
| Merge Sort | n log n | n log n | O(n) |
| Quick Sort | n² | n log n | O(n) or O(log n) |

The next slide gives the average runtimes for the 4 methods on a 1.7G Intel Pentium 4 PC with 512M RAM and Microsoft Visual.NET2003.

For each n at lest 100 randomly generated integer instances were run.

# The following is a plot of average times (milliseconds) for sort methods:

![](img/15e8d7d94d8ddf02cb6839870195a31e_660_0.png)

# For average behavior, we can see:

+   - Quick Sort outperforms the other sort methods for suitably large n.
+   - the break-even point between Insertion and Quick Sort is near 100, let it be nBreak.
+   - when n < nBreak, Insert Sort is the best, and when n > nBreak, Quick Sort is the best.
+   - improve Quick Sort by sorting sublists of less than nBreak records using Insertion Sort.

# Experiments: P435-4

# 7.10 External Sorting

# 7.10.1 introduction

+   - the lists are too large to be entirely contained in the internal memory, making an internal sort impossible.
+   - the lists to be sorted resides on a disk.
+   - block: the unit of data that is read from or written to a disk at one time.
+   - disk --- provide direct access to block, its I/O time is determined by:

+   (1) seek time
+   (2) latency time
+   (3) transmission time

Note I/O rate << CPU rate.

# The most popular method for external sorting is merge sort, which consists of 2 phases:

(1) Segments of the input list are sorted in internal memory, these sorted segments, known as runs, are written onto disk as they are generated.

unsorted => Internal memory => sorted runs

(2) The runs are merged together until only one run left.
