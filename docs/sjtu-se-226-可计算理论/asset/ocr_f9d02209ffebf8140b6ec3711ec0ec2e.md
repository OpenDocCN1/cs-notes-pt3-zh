# An Example

$Q=\{q_s,q_h,q_1,q_2,q_3\}$, $\Gamma=\{0,1,\square,\triangleright\}$,\nand $\delta$ is as follows:

| $p$ | $a$ | $\delta(p,a)$ |
|---|---|---|
| $q_s$ | $0$ | $(q_s,0,\rightarrow)$ |
| $q_s$ | $1$ | $(q_s,1,\rightarrow)$ |
| $q_s$ | $\square$ | $(q_1,\square,\leftarrow)$ |
| $q_s$ | $\triangleright$ | $(q_s,\triangleright,\rightarrow)$ |
| $q_1$ | $0$ | $(q_1,0,\rightarrow)$ |
| $q_1$ | $1$ | $(q_2,\square,\rightarrow)$ |
| $q_1$ | $\square$ | $(q_3,\square,\rightarrow)$ |
| $q_1$ | $\triangleright$ | $(q_h,\triangleright,\rightarrow)$ |
| $q_2$ | $0$ | $(q_4,0,\leftarrow)$ |
| $q_2$ | $1$ | $(q_3,0,\leftarrow)$ |
| $q_2$ | $\square$ | $(q_s,\square,\leftarrow)$ |
| $q_3$ | $0$ | $(q_3,1,\leftarrow)$ |
| $q_3$ | $1$ | $(q_s,1,\leftarrow)$ |
| $q_3$ | $\square$ | $(q_h,\square,\leftarrow)$ |

Start the machine with input 010

+   - $q_s,\triangleright010$
+   - $q_s,\triangleright010$
+   - $q_s,\triangleright010$
+   - $q_s,\triangleright010\square$
+   - $q_1,\triangleright010\square$
+   - $q_1,\triangleright01\square\square$
+   - $q_2,\triangleright01\square\square$
+   - $q_2,\triangleright0\square0\square$
+   - $q_3,\triangleright0\square0\square$
+   - $q_3,\triangleright0\square\square10$