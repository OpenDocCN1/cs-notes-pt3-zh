# # User Threads

+   - User threads are supported above the kernel. The kernel **is not aware** of user threads.
+   - A library provides all support for thread creation, termination, joining, and scheduling.
+   - There is no kernel intervention, and, hence, user threads are usually **more efficient**.
+   - Unfortunately, since the kernel only recognizes the containing process (of the threads), _if one thread is blocked, every other threads of the same process are also blocked_ because the containing process is blocked.