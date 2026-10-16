# Analysis of Merge:

At each iteration of the for loop, either i1++ or i2++, the for loop is iterated at most n-l+1 times.

At most n-l+1 records are copied.

The total time: O(n-l+1).

If each record has a size s, then the total time is O(s(n-l+1)).

When s>1, use linked lists, only need n-l+1 links, the merge time becomes O(n-l+1) and is independent of s.