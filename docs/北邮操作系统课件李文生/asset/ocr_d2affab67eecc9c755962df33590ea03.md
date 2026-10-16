# Dispatcher

+   ▪ Dispatcher module gives control of the CPU to the process selected by the short-term scheduler; this involves:
+     - switching context
+     - switching to user mode
+     - jumping to the proper location in the user program to restart that program

+   ▪ *Dispatch latency* – time it takes for the dispatcher to stop one process and start another running.