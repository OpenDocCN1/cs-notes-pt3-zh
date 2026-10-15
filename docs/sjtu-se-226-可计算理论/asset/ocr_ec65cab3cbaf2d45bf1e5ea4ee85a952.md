# Definition by Case

# Proposition

Suppose that $f_1(\vec{x}),...,f_k(\vec{x})$ are primitive recursive functions, and $M_1(\vec{x}),...,M_k(\vec{x})$ are primitive recursive predicates, such that for every $\vec{x}$ exactly one of $M_1(\vec{x}),...,M_k(\vec{x})$ holds. Then the function $g(\vec{x})$ given by

$g(\vec{x}) = \begin{cases} f_1(\vec{x}), & \text{if } M_1(\vec{x}) \text{ holds}, \\ f_2(\vec{x}), & \text{if } M_2(\vec{x}) \text{ holds}, \\ \vdots \\ f_k(\vec{x}), & \text{if } M_k(\vec{x}) \text{ holds}. \end{cases}$

is primitive recursive.

# Proof

$g(\vec{x}) = c_{M_1}(\vec{x})f_1(\vec{x}) + ... + c_{M_k}(\vec{x})f_k(\vec{x})$