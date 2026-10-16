# 16.3.3 Correctness of Huffman’s algorithm

# Theorem 16.4
Procedure HUFFMAN produces an optimal prefix code.

Proof Immediate from Lemmas 16.2（每一次选择是贪婪的、是正确的）and Lemmas 16.3（确保由子问题的最优解能导出原问题的最优解）。