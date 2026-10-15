# Guidelines and Observations

+   1. The decision table technique is indicated for applications characterized by any of the following:
+      a. Prominent if–then–else logic
+      b. Logical relationships among input variables
+      c. Calculations involving subsets of the input variables
+      d. Cause-and-effect relationships between inputs and outputs
+      e. High cyclomatic complexity (see Chapter 9)

+   2. Decision tables do not scale up very well (a limited entry table with n conditions has 2ⁿ rules).

+   3. The first set of conditions and actions you identify may be unsatisfactory. Use it as a stepping stone and gradually improve on it until you are satisfied with a decision table.