# # 7.4.3 Heap Management

+   - A standard method for maintaining the heap and implementing these functions:
+   
+   (1) a circular linked list of free blocks.
+   (2) memory is taken by malloc.
+   (3) memory is return by free.

+   - drawbacks:
+   
+   (1) The free operation can not tell if the pointer is legal or not.
+   
+   (2) Care must be taken to coalesce blocks otherwise, the heap can quickly become fragmented.