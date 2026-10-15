# 自由存储小结

+   - 使用delete和delete[]释放空间
+     - delete和delete[]把使用new操作分配的内存空间还给自由存储，释放的空间可以用于新的分配
+     - `delete pi; // 释放单个对象`
+     - `delete pc; // 释放单个对象`
+     - `delete[] pd;     // 释放数组`
+     - 释放零值的指针（null指针）的操作不会做任何事情
+     - `char* p = 0;`
+     - `delete p; // 无害的`