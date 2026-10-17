# # 定理9.2

设 \(\circ\) 为 \(S\) 上可结合的二元运算，\(e\) 为该运算的单位元，对于 \(x \in S\) 如果存在左逆元 \(y_l\) 和右逆元 \(y_r\)，则有 \(y_l = y_r = y\)，且 \(y\) 是 \(x\) 的惟一的逆元。

证：由 \(y_l \circ x = e\) 和 \(x \circ y_r = e\) 得

\(y_l = y_l \circ e = y_l \circ (x \circ y_r) = (y_l \circ x) \circ y_r = e \circ y_r = y_r\)

令 \(y_l = y_r = y\)，则 \(y\) 是 \(x\) 的逆元。

假若 \(y' \in S\) 也是 \(x\) 的逆元，则

\(y' = y' \circ e = y' \circ (x \circ y) = (y' \circ x) \circ y = e \circ y = y\)

所以 \(y\) 是 \(x\) 惟一的逆元。

说明：对于可结合的二元运算，可逆元素 \(x\) 只有惟一的逆元，记作 \(x^{-1}\)