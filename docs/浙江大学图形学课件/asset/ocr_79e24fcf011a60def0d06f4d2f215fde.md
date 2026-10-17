# # NURBS curve

# ## B-spline curve:

\( C(u) = \sum_{i=0}^n P_i N_{i,p}(u) \quad a \leq u \leq b \)

Where \( P_0, P_1, \dots, P_n \) are control points, \( \mathbf{u} = [u_0=a, u_1, \dots, u_i, \dots, u_{n+k+1}=b] \).

\( N_{i,0}(u) = \begin{cases} 1 & u_i \leq u < u_{i+1} \\ 0 & \text{otherwise} \end{cases} \)

\( N_{i,p}(u) = \frac{u - u_i}{u_{i+p} - u_i} N_{i,p-1}(u) + \frac{u_{i+p+1} - u}{u_{i+p+1} - u_{i+1}} N_{i+1,p-1}(u) \)

\( \frac{0}{0} = 0 \)

![](bbox=[0.326, 0.718, 0.695, 0.931])