# C++11 Smart Pointers

+   - C++11 deprecates an older smart pointer template
+     - **auto_ptr** : can guard dynamically allocated memory and pass ownership around, but doesn’t work with the STL containers and has other limitations
+   - C++11 provides 3 new smart pointer templates instead
+     - **shared_ptr** : a general purpose reference counted guard for dynamic memory (we’ll mostly use this one in this course)
+     - **weak_ptr** : gives access to a resource that is guarded by a shared_ptr without increasing reference count (can be used to prevent memory leaks due to circular references)
+     - **unique_ptr** : a more complex but potentially very efficient way to transfer ownership of dynamic memory safely (implements C++11 “move semantics”)