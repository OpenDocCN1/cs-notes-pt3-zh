# # Maximum likelihood technique
- 极大似然技术

Since \( B^m \) has \( 2^m \) elements, there are \( 2^m \) code words in \( B^n \). List it as

\( x^{(1)}, x^{(2)}, \dots, x^{(2^m)} \)

If the received word is \( x_t \), we compute \( \delta(x^{(i)}, x_t) \) for \( 1 \leq i \leq 2^m \), and choose the first code word, say it is \( x^{(s)} \), such that

\( \min_{1 \leq i \leq 2^m} \{ \delta(x^{(i)}, x_t) \} = \delta(x^{(s)}, x_t) \)