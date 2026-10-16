# # Example 5

If \(x_t = 001110\), then \(f_H(x_t) = x_t * \mathbf{H} = 101\), same as \(\varepsilon=010000\).

\(x = x_t \oplus \varepsilon = 001110 \oplus 010000 = 011110 = e(011)\), so decode 001110 as 011.

| Syndrome of Coset Leader | Coset leader |
|--------------------------|--------------|
| 000                      | 000000       |
| 001                      | 000001       |
| 010                      | 000010       |
| 011                      | 001000       |
| 100                      | 000100       |
| 101                      | 010000       |
| 110                      | 100000       |
| 111                      | 001100       |