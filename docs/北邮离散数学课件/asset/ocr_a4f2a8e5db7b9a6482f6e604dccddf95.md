# # Coset leader – 陪集头

Suppose that the code word \( x = e(b) \) is transmitted
and that the word \( x_t \) is received.

The left coset of \( x_t \) is

\( x_t \oplus \text{N} = \{ \varepsilon_1, \varepsilon_2, \dots, \varepsilon_{2m} \} \quad \text{where} \quad \varepsilon_i = x_t \oplus x^{(i)} \)

if \( \varepsilon_j \) is a coset member with smallest weight, then \( x^{(j)} \)
must be a code word that is closest to \( x_t \).

An element \( \varepsilon_j \), having smallest weight, is called a
_coset leader_.