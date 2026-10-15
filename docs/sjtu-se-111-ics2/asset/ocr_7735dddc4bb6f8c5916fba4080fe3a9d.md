# VM as a Tool for Memory Protection

+   - Page fault handler checks these before remapping
+     - If violated, send process SIGSEGV (segmentation fault)

Process i:

|  | SUP | READ | WRITE | Address |
|---|---|---|---|---|
| VP 0: | No | Yes | No | PP 6 |
| VP 1: | No | Yes | Yes | PP 4 |
| VP 2: | Yes | Yes | Yes | PP 2 |

Physical Address Space

Process j:

|  | SUP | READ | WRITE | Address |
|---|---|---|---|---|
| VP 0: | No | Yes | No | PP 9 |
| VP 1: | Yes | Yes | Yes | PP 6 |
| VP 2: | No | Yes | Yes | PP 11 |

![](bbox=[0.65, 0.42, 0.92, 0.92])