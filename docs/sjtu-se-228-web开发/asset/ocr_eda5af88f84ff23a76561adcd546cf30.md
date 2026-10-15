# Configuration

+   - The `struts.xml` File
+     - The `Package` Tag.
+       - is used to group together configurations that share common attributes such as interceptor stacks or URL namespaces.
+       - The attributes for this tag are:
+         - **name** – a developer provided unique name for this package
+         - **extends** – the name of a package that this package will extend
+         - **namespace** – the namespace provides a mapping from the URL to the package.
+         - **abstract** – if this attribute value is “true” the package is truly configuration grouping, and actions configured will not be accessible via the package name