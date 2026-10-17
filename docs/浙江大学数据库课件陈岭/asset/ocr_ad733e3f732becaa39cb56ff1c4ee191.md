# # Testing if an Attribute is Extraneous

(实际算法)

# ## To test if attribute \( A \in \alpha \) is extraneous in \( \alpha \)

+   1. compute \( (\alpha - A)^+ \) using the dependencies in \( F \)

+   2. check that \( (\alpha - A)^+ \) contains \( \beta \);

if it does, \( A \) is extraneous

# ## To test if attribute \( A \in \beta \) is extraneous in \( \beta \)

+   1. compute \( \alpha^+ \) using only the dependencies in \( F' \)

\( F' = (F - \{ \alpha \to \beta \}) \cup \{ \alpha \to (\beta - A) \} \)

+   2. check that \( \alpha^+ \) contains \( A \); if it does, \( A \) is extraneous

![](bbox=[0.691, 0.266, 0.984, 0.398])

![](bbox=[0.582, 0.641, 0.93, 0.797])

![](bbox=[0.0, 0.82, 0.078, 0.969])

![](bbox=[0.82, 0.789, 1.0, 0.984])