# The correctness can be verified by induction.

![](bbox=[0.049, 0.163, 0.504, 0.404])

Let us run Copy for A = ((a, b), ((c, d), e)) as in the next slide.

# Computing time:

+   - nodes with tag==false, visited twice.
+   - nodes with tag==true visited three times.
+   
+   If the list has m nodes, the time is O(m).