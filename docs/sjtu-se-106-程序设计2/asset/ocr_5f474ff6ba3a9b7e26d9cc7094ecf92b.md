# Selection Sort Running Times

+   - Many algorithms that operate on vectors have running times that are proportional to the size of the array. If you multiply the number of values by ten, you would expect those algorithms to take ten times as long.
+   - As the running times on the preceding slide make clear, the situation for selection sort is very different. The table on the right shows the average running time when selection sort is applied to 10, 100, 1000, and 10000 values.
+   - As a rough approximation—particularly as you work with larger values of N—it appears that every ten-fold increase in the size of the array means that selection sort takes about 100 times as long.

| N | time |
|---|------|
| 10 | .0024 |
| 100 | 0.162 |
| 1000 | 14.32 |
| 10000 | 1332. |