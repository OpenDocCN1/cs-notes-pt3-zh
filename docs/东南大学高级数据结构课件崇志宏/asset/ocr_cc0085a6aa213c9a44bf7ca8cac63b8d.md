# Data Structure and Algorithm

# Stable Matching Problem

Perfect matching: everyone is matched monogamously.

+   - Each man gets exactly one woman.
+   - Each woman gets exactly one man.

Stability: no incentive for some pair of participants to undermine assignment by joint action.

+   - In matching M, an unmatched pair m-w is unstable if man m and woman w prefer each other to current partners.
+   - Unstable pair m-w could each improve by eloping.

Stable matching: perfect matching with no unstable pairs.

Stable matching problem. Given the preference lists of n men and n women, find a stable matching if one exists.