# # Tighter analysis

Let \(c_i=\) the cost of the \(i\)th insertion
\(=\left\{\begin{array}{ c c }
i & \text{if } i-1 \text{ is an exact power of } 2, \\
1 & \text{otherwise.}
\end{array}\right.\)

|    | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
|---|---|---|---|---|---|---|---|---|---|---|
| \(i\)   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| \(size_i\) | 1   | 2   | 4   | 4   | 8   | 8   | 8   | 8   | 16  | 16  |
| \(c_i\)   | 1   | 2   | 3   | 1   | 5   | 1   | 1   | 1   | 9   | 1   |