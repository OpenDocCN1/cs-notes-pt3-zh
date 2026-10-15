# Internal Consistency: finding security holes

Applications are bad:

+   - Rule: “do not dereference user pointer <p>”
+   - One violation = security hole
+   - Big Problem: which are the user pointers???

Sol’n: forall pointers, cross-check two OS beliefs

+   - “*p” implies safe kernel pointer
+   - “copyin(p)/copyout(p)” implies dangerous user pointer
+   - Error: pointer p has both beliefs.