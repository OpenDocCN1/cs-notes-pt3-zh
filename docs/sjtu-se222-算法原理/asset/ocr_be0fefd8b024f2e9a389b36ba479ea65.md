# LSD string sort: correctness proof

Proposition. LSD sorts fixed-length strings in ascending order.

Pf. [ by induction on i ]

After pass i, strings are sorted by last i characters.

+   - If two strings differ on sort key, key-indexed sort puts them in proper relative order.
+   - If two strings agree on sort key, stability keeps them in proper relative order.

![](bbox=[0.58, 0.38, 0.88, 0.92])

Proposition. LSD sort is stable.

Pf. Key-indexed counting is stable.