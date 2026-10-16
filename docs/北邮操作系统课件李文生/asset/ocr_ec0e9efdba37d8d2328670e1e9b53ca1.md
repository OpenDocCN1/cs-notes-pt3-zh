# System Call Parameter Passing

+   - Often, more information is required than simply identity of desired system call
+     - Exact type and amount of information vary according to OS and call
+   - Three general methods used to pass parameters to the OS
+     - Simplest: pass the parameters in *registers*
+       - In some cases, may be more parameters than registers
+     - Parameters stored in a *block*, or table, in memory, and address of block passed as a parameter in a register
+       - This approach taken by Linux and Solaris
+     - Parameters placed, or *pushed*, onto the *stack* by the program and *popped* off the stack by the operating system
+     ( Block and stack methods do not limit the number or length of parameters being passed )