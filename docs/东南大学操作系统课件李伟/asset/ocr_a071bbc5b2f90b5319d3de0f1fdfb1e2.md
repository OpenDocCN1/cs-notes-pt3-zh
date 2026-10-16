# Performance of Demand Paging

+   - **Page Fault Rate** 0 ≤ p ≤ 1
+     - if p = 0 no page faults
+     - if p = 1, every reference is a fault

+   - **Effective Access Time (EAT)**
+     EAT = (1 − p) x memory access time
+     + p (page fault overhead)
+     page fault overhead = service the page-fault interrupt
+     + [swap page out]
+     + swap page in
+     + restart overhead