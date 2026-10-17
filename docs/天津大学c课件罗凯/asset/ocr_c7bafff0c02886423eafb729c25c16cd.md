# Giving back the memory

+   - Forms of request

```
delete ptr;        // if storage came from new
delete [] arrPtr;  // if storage came from new[]
```

+   - Storage pointed to by ptr and arrPtr is returned to free store
+     - ptr and arrPtr are now undefined