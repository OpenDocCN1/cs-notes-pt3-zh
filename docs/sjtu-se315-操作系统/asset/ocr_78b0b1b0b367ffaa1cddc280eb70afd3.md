# Linus’ Response

http://linux-kernel.2935.n7.nabble.com/PATCH-v5-0-5-x86-smp-make-ticket-spinlock-proportional-backoff-w-auto-tuning-td596698i20.html

So I claim:

+   - it's *really* hard to trigger in real loads on common hardware.
+   - if it does trigger in any half-way reasonably common setup (hardware/software), we most likely should work really hard at fixing the underlying problem, not the symptoms.
+   - we absolutely should *not* pessimze the common case for this