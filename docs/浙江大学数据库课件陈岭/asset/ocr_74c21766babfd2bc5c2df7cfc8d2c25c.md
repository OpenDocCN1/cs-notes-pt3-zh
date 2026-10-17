# # (1) Select Operation(cont.)

+   - Notation: \(\sigma_p(r)\), \(\sigma\) is pronounced as sigma

+   - **_p_** is called the **selection predicate**

+   - Defined as: \(\sigma_p(r) = \{ t \mid t \in r \text{ and } p(t) \}\)

Where **_p_** is a formula in propositional calculus consisting of **terms** connected by: \(\land\) (and), \(\lor\) (or), \(\neg\) (not)

Each **term** is one of:

<attribute> **_op_** <attribute> or <constant>

where **_op_** is one of: =, \(\neq\), >, \(\geq\), <, \(\leq\)

+   - Example of selection:

\(\sigma_{\text{branch-name}=\text{'Perryridge'}}(\text{account})\)