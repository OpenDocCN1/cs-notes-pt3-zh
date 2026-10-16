# How good is BCNF? (Cont.)

+   - There are no non-trivial functional dependencies and therefore the relation is in BCNF
+   - Insertion anomalies – i.e., if we add a phone 981-992-3443 to 99999, we need to add two tuples
+     (99999, David,  981-992-3443)
+     (99999, William, 981-992-3443)