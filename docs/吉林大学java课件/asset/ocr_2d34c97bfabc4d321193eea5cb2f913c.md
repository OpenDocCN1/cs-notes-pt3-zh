# Thread类和Runnable接口的区别

+   实际上Thread类和Runnable接口之间在使用上也是有所区别的，如果一个类继承Thread类，则不适合于多个线程共享资源，而实现了Runnable接口，则可以方便的实现资源的共享。