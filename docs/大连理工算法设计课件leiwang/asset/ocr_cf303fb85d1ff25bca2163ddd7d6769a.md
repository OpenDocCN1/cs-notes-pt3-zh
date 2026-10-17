# # Hairy recurrence

(But not quite as hairy as the quicksort one.)

\(E[T(n)] = \frac{2}{n} \sum_{k=\lfloor n/2 \rfloor}^{n-1} E[T(k)] + \Theta(n)\)

**Prove:** \(E[T(n)] \le cn\) for constant \(c > 0\).

+   • The constant \(c\) can be chosen large enough so that \(E[T(n)] \le cn\) for the base cases.

**Use fact:** \(\sum_{k=\lfloor n/2 \rfloor}^{n-1} k \le \frac{3}{8}n^2\) (exercise).