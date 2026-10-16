# # Example 2

Consider the \((m, 3m)\) encoding function defined in Example 3 of Section 11.1. Define the decoding function \(d: B^m \to B^{3m}\).

Let \(y = Y_1Y_2 \cdots Y_m Y_{m+1} \cdots Y_{2m} Y_{2m+1} \cdots Y_{3m}\), Then

\(d(y) = z_1z_2 \cdots z_m\)

where

\(z_i = \begin{cases} 1 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has at least two 1's} \\ 0 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has less than two 1's} \end{cases}\)

E.g. \(x_t = 011011111\), then \(d(x_t) = 011\)