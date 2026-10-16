# 3PC: Handling Site Failure (Cont.)

+   - Log contains <precommit T> record, but no <abort T> or <commit T>: site consults Ci to determine the fate of T.
+     - if Ci says T aborted, site executes **undo** (T)
+     - if Ci says T committed, site executes **redo** (T)
+     - if Ci says T still in precommit state, site resumes protocol at this point
+   - Log contains no <ready T> record for a transaction T: site executes **undo** (T) writes <abort T> record