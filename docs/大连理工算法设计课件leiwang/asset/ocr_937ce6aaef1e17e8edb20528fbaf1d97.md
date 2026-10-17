# # Merge sort

# ## MERGE-SORT \( A[1 \dots n] \)

+   1. If \( n = 1 \), done.

+   2. Recursively sort \( A[1 \dots \lceil n/2 \rceil] \) and \( A[\lceil n/2 \rceil+1 \dots n] \).

+   3. **“Merge”** the 2 sorted lists.

# ### Key subroutine: MERGE

September 7, 2005

Copyright © 2001-5 Erik D. Demaine and Charles E. Leiserson Introduction to Algorithms

L1.25