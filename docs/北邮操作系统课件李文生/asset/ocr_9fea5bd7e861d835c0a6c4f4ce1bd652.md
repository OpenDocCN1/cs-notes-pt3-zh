# 5.5 Thread Scheduling

# Threads

+   - Executes separate from the rest of the process
+   - An application can be a set of threads that cooperate and execute concurrently in the same address space
+   - Threads running on separate processors yields a dramatic gain in performance

# Thread Scheduling

+   - Local Scheduling – How the threads library decides which user-level thread to put onto an available LWP. m:1 and m:n model, process-contention scope (PCS)
+   - Global Scheduling – How the kernel decides which kernel thread to run next. System-contention scope (SCS) 1:1 model uses only SCS.