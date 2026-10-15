# Position-Independent Code (PIC)

+   - PIC Function Calls
+     ```
+     call      L1
+     L1:    popl  %ebx
+     addl      $PROCOFF, $ebx
+     call      *(%ebx)
+     ```
+     - Performance disadvantages (3 instr)
+     - Optimization: lazy binding