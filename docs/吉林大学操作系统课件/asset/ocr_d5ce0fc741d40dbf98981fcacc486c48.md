# Java synchronization rules

A thread that owns the lock for an object can enter another synchronized method (or block) for the same object.

+   - A method can nest synchronized method invocation for different objects. Thus a thread cab simultaneously own the lock for several different objects.
+   - If a method is not declared as synchronized, then it can be invoked regardless of lock ownership, even while another synchronized method for the same object is executing.
+   - If the wait set for an object is empty, then a call to notify() or notifyAll() has no effect.