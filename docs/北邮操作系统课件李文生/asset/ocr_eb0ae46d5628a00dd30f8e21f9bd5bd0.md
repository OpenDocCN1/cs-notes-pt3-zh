# Supplement:
problem and solution (cont.): Spooling

+   - **S**imultaneous **P**eripheral **O**peration **O**n **L**ine
+   - Overlap I/O of one job with computation of another job. While executing one job, the OS.
+     - Reads next job from card reader into a storage area on the disk (job queue).
+     - Outputs printout of previous job from disk to printer.
+   - *Job pool* – data structure that allows the OS to select which job to run next in order to increase CPU utilization.