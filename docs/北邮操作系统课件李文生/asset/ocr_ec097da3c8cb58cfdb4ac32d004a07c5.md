# LRU implementation

+   Stack – keep a stack of page numbers in a double link form:
+   - Page referenced:
+     - move it to the top
+     - requires 6 pointers to be changed
+   - No search for replacement

+   example: 4 7 0 7 1 0 1 2 1 2 7 1 2

![](bbox=[0.12, 0.55, 0.97, 0.97])