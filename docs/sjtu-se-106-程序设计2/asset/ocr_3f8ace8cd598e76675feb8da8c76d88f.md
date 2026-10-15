# Hash Functions

+   - A hash function is denoted by
+     h: {0, 1}* → {0, 1}^n
+     where n is a security parameter, say 128, 160, 256 or 512.
+   - In English:
+     - A function which is applicable to data of any size.
+     - Its produces a fixed length output, usually short.
+   - 3 Types of Security Requirements:
+     - One-way: given an output z, it is difficult to find x such that z = h(x).
+     - Weak collision-resistant: given x, it is difficult to find y ≠ x such that h(y) = h(x).
+     - Strong collision-resistant: it is difficult to find any pair (x, y) such that h(x) = h(y).
+   - Note: Strong collision-resistant ⇒ Weak collision-resistant ⇒ One-way
+   - Let m be some message. h(x) is called the message digest.