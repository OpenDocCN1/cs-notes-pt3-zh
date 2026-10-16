# Security with External Language Routines

+   - To deal with security problems, we can do on of the following:
+     - Use **sandbox** techniques
+       - That is, use a safe language like Java, which cannot be used to access/damage other parts of the database code.
+     - Run external language functions/procedures in a separate process, with no access to the database process’ memory.
+       - Parameters and results communicated via inter-process communication
+   - Both have performance overheads
+   - Many database systems support both above approaches as well as direct executing in database system address space.