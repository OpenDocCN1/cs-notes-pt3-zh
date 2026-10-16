# Thread Cancellation

+   - int pthread_setcancelstate(int state, int *oldstate);
+     - PTHREAD_CANCEL_ENABLE
+     - PTHREAD_CANCEL_DISABLE
+   - int pthread_setcanceltype(int type, int *oldtype);
+     - PTHREAD_CANCEL_ASYNCHRONOUS
+     - PTHREAD_CANCEL_DEFERRED
+   - void pthread_testcancel(void);