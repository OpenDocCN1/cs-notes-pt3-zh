# 7.5 Deadlock Avoidance

Requires that the system has some additional *a priori* information available.

Processes under consideration must be independent; No synchronization requirements.

+   - Simplest and most useful model requires that each process declare the *maximum number* of resources of each type that it may need.
+   - The **deadlock-avoidance algorithm** dynamically examines the resource-allocation state to ensure that there can never be a circular-wait condition.
+   - **Resource-allocation state** is defined by the number of available and allocated resources, and the maximum demands of the processes.