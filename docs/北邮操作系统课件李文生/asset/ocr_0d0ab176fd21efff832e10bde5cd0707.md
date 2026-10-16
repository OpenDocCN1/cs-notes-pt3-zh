# UNIX System Structure

+   - **UNIX – limited by hardware functionality, the original UNIX operating system had limited structuring.**
+   - **The UNIX OS consists of two separable parts**
+     - System programs
+     - The kernel, which is further separated into a series of interfaces and device drivers.
+       - Consists of everything below the system-call interface and above the physical hardware
+       - Provides the file system, CPU scheduling, memory management, and other operating-system functions; a large number of functions for one level.
+   - **System calls define the API to UNIX, the set of system programs commonly available defines the user interface.**