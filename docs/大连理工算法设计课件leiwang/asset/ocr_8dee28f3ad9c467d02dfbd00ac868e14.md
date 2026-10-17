# # Divide-and-conquer algorithm

# ## IDEA:

$n\times n$ matrix = $2\times 2$ matrix of $(n/2)\times(n/2)$ submatrices:

\(\left[\begin{array}{ c c }
r & s \\
t & u
\end{array}\right] = \left[\begin{array}{ c c }
a & b \\
c & d
\end{array}\right] \cdot \left[\begin{array}{ c c }
e & f \\
g & h
\end{array}\right]\)

\(C = A \cdot B\)

\(\left.\begin{array}{ l }
r = ae + bg \\
s = af + bh \\
t = ce + dg \\
u = cf + dh
\end{array}\right\}\)

8 mults of $(n/2)\times(n/2)$ submatrices
4 adds of $(n/2)\times(n/2)$ submatrices