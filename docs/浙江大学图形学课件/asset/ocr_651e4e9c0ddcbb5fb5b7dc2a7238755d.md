# Computing View Depth

![](bbox=[0.18, 0.21, 0.82, 0.49])

For a perspective view, it is not that simple. For example, n2 > n1 does not automatically imply that P4 obscures P3. It has to project on the same pixel that is it should be farther away on the same projector. We must compare:

$$\frac{u_1}{n_1}=\frac{u_2}{n_2} \quad \text{and also} \quad \frac{v_1}{n_1}=\frac{v_2}{n_2}$$