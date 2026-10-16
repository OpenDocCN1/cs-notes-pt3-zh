# Theory of the Strategy Pattern

# 2. Easy extension

Encapsulating the algorithm in separate Strategy classes lets you change the algorithm independently of its context, making it easier to

+   - understand,
+   - switch (change to a more efficient algorithm)
+   - extend.

+   - When an existing algorithm implementation is changed or a new algorithm is added to the group, both the existing strategy class hierarchy and the context remain unaffected.