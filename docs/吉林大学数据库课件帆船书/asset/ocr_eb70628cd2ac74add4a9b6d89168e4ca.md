# BCNF and Dependency Preservation

+   - Constraints, including functional dependencies, are costly to check in practice unless they pertain to only one relation
+   - If it is sufficient to test only those dependencies on each individual relation of a decomposition in order to ensure that *all* functional dependencies hold, then that decomposition is *dependency preserving*.
+   - Because it is not always possible to achieve both BCNF and dependency preservation, we consider a weaker normal form, known as *third normal form*.