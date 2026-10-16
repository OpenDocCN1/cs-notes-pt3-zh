# Workflow Management System Architectures

+   - **Centralized** - a single scheduler schedules the tasks for all concurrently executing workflows.
+     - used in workflow systems where the data is stored in a central database.
+     - easier to keep track of the state of a workflow.

+   - **Partially distributed** - has one (instance of a) scheduler for each workflow.

+   - **Fully distributed** - has no scheduler, but the task agents coordinate their execution by communicating with each other to satisfy task dependencies and other workflow execution requirements.
+     - used in simplest workflow execution systems
+     - based on electronic mail