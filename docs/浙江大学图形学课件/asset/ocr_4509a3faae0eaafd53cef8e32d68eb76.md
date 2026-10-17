# # subdivision surface

# # Catmull-Clerk and Doo-Sabin subdivision

start from

\(P^i = \left(\cdots, p_{-1}^i, p_0^i, p_1^i, p_2^i, \cdots\right)\)

# ## Catmull-Clerk rules

\(p_{2j}^{i+1} = \frac{1}{8}p_{j-1}^i + \frac{6}{8}p_j^i + \frac{1}{8}p_{j+1}^i\)
\(p_{2j+1}^{i+1} = \frac{4}{8}p_j^i + \frac{4}{8}p_{j+1}^i\)

# ## Doo-Sabin rules:

\(p_{2j}^{i+1} = \frac{3}{4}p_j^i + \frac{1}{4}p_{j+1}^i\)
\(p_{2j+1}^{i+1} = \frac{1}{4}p_j^i + \frac{3}{4}p_{j+1}^i\)

![](bbox=[0.598, 0.513, 0.932, 0.703])

Figure 3: Subdividing an initial set of control points (upper, red) results in additional control points (lower, black), that more closely approximate a curve.