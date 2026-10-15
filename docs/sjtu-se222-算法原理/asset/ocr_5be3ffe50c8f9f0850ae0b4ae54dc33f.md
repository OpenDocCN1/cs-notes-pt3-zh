# Summary: sorting algorithms

| algorithm | guarantee | random | extra space | stable? | operations on keys |
|---|---|---|---|---|---|
| insertion sort | ½ N² | ¼ N² | 1 | ✔ | compareTo() |
| mergesort | N lg N | N lg N | N | ✔ | compareTo() |
| quicksort | 1.39 N lg N * | 1.39 N lg N | c lg N |  | compareTo() |
| heapsort | 2 N lg N | 2 N lg N | 1 |  | compareTo() |
| LSD sort † | 2 W (N + R) | 2 W (N + R) | N + R | ✔ | charAt() |
| MSD sort ‡ | 2 W (N + R) | N log_R N | N + D R | ✔ | charAt() |

* probabilistic
† fixed-length W keys
‡ average-length W keys

D = function-call stack depth (length of longest prefix match)