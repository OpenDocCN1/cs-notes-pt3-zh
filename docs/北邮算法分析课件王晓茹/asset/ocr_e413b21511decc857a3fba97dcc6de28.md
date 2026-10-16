# 渐近分析记号的若干性质

# （1）传递性：

+   - $f(n)=\Theta(g(n))$, $g(n)=\Theta(h(n)) \Rightarrow f(n)=\Theta(h(n))$;
+   - $f(n)=O(g(n))$, $g(n)=O(h(n)) \Rightarrow f(n)=O(h(n))$;
+   - $f(n)=\Omega(g(n))$, $g(n)=\Omega(h(n)) \Rightarrow f(n)=\Omega(h(n))$;
+   - $f(n)=o(g(n))$, $g(n)=o(h(n)) \Rightarrow f(n)=o(h(n))$;
+   - $f(n)=\omega(g(n))$, $g(n)=\omega(h(n)) \Rightarrow f(n)=\omega(h(n))$;