# Triple Fault

+   - Things never to do in an OS #1: Swap out the page swapping code (triple-fault here we come) —Kemp
+   - When a fault occurs, the CPU invokes an exception handler.
+   - If a fault occurs while trying to invoke the exception handler, that's called a double fault, which the CPU tries to handle with yet another exception handler.
+   - If that invocation results in a fault too, the system reboots with a triple fault.