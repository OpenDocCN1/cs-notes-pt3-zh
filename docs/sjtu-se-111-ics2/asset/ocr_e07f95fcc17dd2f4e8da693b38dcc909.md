# Classes of Data Hazards

+   - **Program states:**
+     - Program registers (identified)
+     - Condition codes (**No hazards**)
+       - Both written and read in the execute stage.
+     - Program counter (section 4.5.11)
+       - Conflicts between updating and reading PC cause control hazards (e.g. mispredicted branches and `ret`)
+     - Memory
+       - Both written and read in the memory stage.
+       - Without _self-modified_ code, **no hazards**.
+     - Status register (section 4.5.9)
+       - Orderly halt when an exception occurs