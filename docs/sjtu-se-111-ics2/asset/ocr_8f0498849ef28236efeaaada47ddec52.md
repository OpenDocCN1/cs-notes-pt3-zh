# Mapping Variable Instances to Memory

+   - Global variables
+     - Def: Variable declared outside of a function
+     - Virtual memory contains exactly one instance of any global variable
+   - Local variables
+     - Def: Variable declared inside function without static attribute
+     - Each thread stack contains one instance of each local variable
+   - Local static variables
+     - Def: Variable declared inside function with the static attribute
+     - Virtual memory contains exactly one instance of any local static variable.