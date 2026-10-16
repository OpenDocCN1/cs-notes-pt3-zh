# Merge-Join (Cont.)

+   - Can be used only for equi-joins and natural joins
+   - Each block needs to be read only once (assuming all tuples for any given value of the join attributes fit in memory
+   - Thus the cost of merge join is:
+     $b_r + b_s$ block transfers + $\lceil b_r / b_b \rceil + \lceil b_s / b_b \rceil$ seeks
+     - + the cost of sorting if relations are unsorted.
+   - hybrid merge-join: If one relation is sorted, and the other has a secondary B⁺-tree index on the join attribute
+     - Merge the sorted relation with the leaf entries of the B⁺-tree .
+     - Sort the result on the addresses of the unsorted relation’s tuples
+     - Scan the unsorted relation in physical address order and merge with previous result, to replace addresses by the actual tuples
+       - Sequential scan more efficient than random lookup