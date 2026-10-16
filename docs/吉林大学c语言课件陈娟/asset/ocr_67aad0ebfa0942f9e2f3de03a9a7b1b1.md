# 例

+   - 申请
+     ```c
+     float *p;
+     p = (float*)malloc( sizeof(float) );
+     struct date *pdate;
+     pdate=(struct date*)malloc(sizeof(struct date));
+     ```
+   - 释放
+     ```c
+     free(p);
+     free(pdate);
+     ```