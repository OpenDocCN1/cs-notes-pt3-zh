# Workflow Scheduler

+   - Ideally scheduler should execute a workflow only after ensuring that it will terminate in an acceptable state.
+   - Consider a workflow consisting of two tasks S₁ and S₂. Let the failure-atomicity requirement be that either both or neither of the subtransactions should be committed.
+     - Suppose systems executing S₁ and S₂ do not provide prepared-to-commit states and S₁ or S₂ do not have compensating transactions.
+     - It is then possible to reach a state where one subtransaction is committed and the other aborted. Both cannot then be brought to the same state.
+     - Workflow specification is unsafe, and should be rejected.
+   - Determination of safety by the scheduler is not possible in general, and is usually left to the designer of the workflow.