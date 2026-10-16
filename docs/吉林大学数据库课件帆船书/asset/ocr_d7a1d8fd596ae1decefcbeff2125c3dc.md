# Transactional Workflows

+   - Must address following issues to computerize a workflow.
+     - Specification of workflows - detailing the tasks that must be carried out and defining the execution requirements.
+     - Execution of workflows - execute transactions specified in the workflow while also providing traditional database safeguards related to the correctness of computations, data integrity, and durability.
+     - E.g.: Loan application should not get lost even if system fails.
+   - Extend transaction concepts to the context of workflows.
+   - State of a workflow - consists of the collection of states of its constituent tasks, and the states (i.e., values) of all variables in the execution plan.