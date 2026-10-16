# 5.1.1 Worst-case analysis

Cost: n candidates, we hire m of them, cost is T(n) = n c_i + m c_h

+   - We focus on analyzing the hiring cost m c_h ? ( c_h >> c_i )

+   - m c_h varies with each run of the algorithm: it depends on the order in which we interview the candidates.

+   - Worst-case analysis

+     - We hire all n candidates. T(n) = n c_i + n c_h ? When?

+     - The candidates appear in increasing order of qulity.

In a month, T(30) = 30 + 30*10 = 330 K

![](bbox=[0.03, 0.64, 0.97, 0.92])