# # Second attempt: using a tuple

n=5, c=10

p= 6 3 5 4 6
w= 2 2 6 5 4
X= x1 x2 x3 x4 x5

+   - Calculate f values using array
+     - f(5,0) = 0, ..., f(5,4) = 6, ..., f(5,10) = 6
+     - f(4,0) = 0, ..., f(4,4) = 6, ..., f(4,9) = 10), f(4,10) = 10
+     - ...

+   - Save step points only for each i
+     - Define a tuple (a, b), where a = y and b = f(i, y)
+     - (a, b) corresponds an optimal loading with capacity a and value b
+     - Put all tuples into a set Pi
+     - Pn can be got easily. Pn = {(0, 0), (wn, pn)}