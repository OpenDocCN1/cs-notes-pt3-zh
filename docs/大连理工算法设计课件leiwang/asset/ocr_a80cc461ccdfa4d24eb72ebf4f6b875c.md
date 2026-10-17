# Analysis (continued)

Recall: Counting sort takes Θ(n + k) time to sort n numbers in the range from 0 to k − 1.

If each b-bit word is broken into r-bit pieces, each pass of counting sort takes Θ(n + 2^r) time. Since there are b/r passes, we have

T(n,b) = Θ( (b/r) (n + 2^r) ).

Choose r to minimize T(n,b):

+   • Increasing r means fewer passes, but as r ≫ lg n, the time grows exponentially.