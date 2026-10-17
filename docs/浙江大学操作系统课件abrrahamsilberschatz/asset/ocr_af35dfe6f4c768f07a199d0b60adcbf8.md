# # Module Management

+   - Supports loading modules into memory and letting them talk to the rest of the kernel.
+   - Module loading is split into two separate sections:
+     - Managing sections of module code in kernel memory
+     - Handling symbols that modules are allowed to reference
+   - The module requestor manages loading requested, but currently unloaded, modules; it also regularly queries the kernel to see whether a dynamically loaded module is still in use, and will unload it when it is no longer actively needed.