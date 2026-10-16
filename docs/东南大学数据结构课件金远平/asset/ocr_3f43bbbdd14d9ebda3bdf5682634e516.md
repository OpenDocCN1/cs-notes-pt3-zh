To distinguish between threads and normal pointers, add two **bool** fields:

+   - `leftThread`
+   - `rightThread`

If `t→leftThread == true`, then `t→leftChild` contains a thread, otherwise a pointer to left child. Similar for `t→rightThread`.