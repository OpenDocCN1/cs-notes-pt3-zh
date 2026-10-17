# # Calculation

**Case 1:** _i_-1 is an exact power of 2.

\(\hat{c}_i = i + 2 - 2^{\lceil \lg i \rceil} + 2^{\lceil \lg (i-1) \rceil}\)
\(= i + 2 - 2(i-1) + (i-1)\)
\(= i + 2 - 2i + 2 + i - 1\)
\(= 3\)

**Case 2:** _i_-1 is _not_ an exact power of 2.

\(\hat{c}_i = 1 + 2 - 2^{\lceil \lg i \rceil} + 2^{\lceil \lg (i-1) \rceil}\)
\(= 3\) (since \(2^{\lceil \lg i \rceil} = 2^{\lceil \lg (i-1) \rceil}\))