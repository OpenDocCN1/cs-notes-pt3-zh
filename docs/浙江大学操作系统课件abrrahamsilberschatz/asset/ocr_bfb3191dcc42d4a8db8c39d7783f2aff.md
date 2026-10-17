# # Example – Bounded Buffer

+   - Shared data:
+   
+   struct buffer {
+   int pool[n];
+   int count, in, out;
+   }