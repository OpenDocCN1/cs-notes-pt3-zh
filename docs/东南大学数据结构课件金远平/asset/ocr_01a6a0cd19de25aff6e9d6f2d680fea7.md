+   - to do k-way merge we need at least k input buffers and 1 output buffer (or the best totally 2k+2).

+   - given fixed internal memory,  
+     k increases => smaller buffer size => more blocks  
+     => increased seek and latency time.

+   - hence, beyond a certain k, I/O time increases despite the decrease in the number of passes.