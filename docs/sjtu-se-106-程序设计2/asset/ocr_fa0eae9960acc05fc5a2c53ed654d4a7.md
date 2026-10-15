# Benefits of Smart Pointers

If an exception occurs within a pointer this means that the remaining code after it will not get executed and in turn the pointer will not get deleted with the potential of memory leaks occurring.

However the use of a smart pointer will remove this threat due to the automatic clean up of the pointer because the pointer will be cleaned up whenever it gets out of scope, whether it was during the normal path of execution or during an exception.

This solution is possible to write for normal pointers; however it is much simpler to implement using smart pointers