# The Readers-Writers Problem

+   - Readers: only read the content of the shared object.
+   - Writers: may update the content of the shared object.
+   - The writers have exclusive access to the shared object.
+   - the first readers-writers problem: reader first
+     - no reader will be kept waiting unless a writer has already obtained permission to use the shared object.
+     - Writers may starve.
+   - the second readers-writers problem: writer first
+     - once a writer is ready, that writer performs its write as soon as possible.
+     - Readers may starve.