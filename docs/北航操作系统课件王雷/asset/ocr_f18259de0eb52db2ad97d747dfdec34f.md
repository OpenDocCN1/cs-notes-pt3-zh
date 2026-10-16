+   - user threads是在使用者空间,透过library模拟的 thread,不需要或仅需要极少的kernel支援,context switching比较快,因为不用更改page table等等东西,使用起来较为轻便快速.user threads提供操控视窗系统的绝佳解决方案.
+   - Examples
+     - POSIX Pthreads
+     - Mach C-threads