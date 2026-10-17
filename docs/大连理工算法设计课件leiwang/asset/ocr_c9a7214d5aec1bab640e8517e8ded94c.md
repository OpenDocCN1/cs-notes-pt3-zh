![](bbox=[0.041, 0.044, 0.151, 0.214])

# # Analysis of Strassen

$T(n)=7T(n/2)+\Theta(n^2)$

$n^{\log_b a}=n^{\log_2 7}\approx n^{2.81}\Rightarrow \text{CASE 1}\Rightarrow T(n)=\Theta(n^{\lg 7})$.