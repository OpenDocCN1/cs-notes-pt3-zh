# Another Fast Path Example

+   - Consider a request stream of different types
+   - Some are very simple and some are very complex
+   - Optimization:
+     ```
+     if (FastPath(request)) {
+         Handle simple cases in highly optimized code
+     } else {
+         Handle request in full generality
+     }
+     ```