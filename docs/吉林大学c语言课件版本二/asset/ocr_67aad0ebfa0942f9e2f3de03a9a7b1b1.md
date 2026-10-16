# 例

+   - 申请
+     ```
+     float *p;
+     p = (float*)malloc( sizeof(float) );
+     struct date *pdate;
+     pdate=(struct date*)malloc(sizeof(struct date));
+     ```
+   - 释放
+     ```
+     free(p);
+     free(pdate);
+     ```