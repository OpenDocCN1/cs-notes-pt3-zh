# Legacy Systems (Cont.)

+   **Chicken-little approach:**
+   - Replace legacy system one piece at a time
+   - Use wrappers to interoperate between legacy and new code
+     - E.g., replace front end first, with wrappers on legacy backend
+       - Old front end can continue working in this phase in case of problems with new front end
+     - Replace back end, one functional unit at a time
+       - All parts that share a database may have to be replaced together, or wrapper is needed on database also
+   - Drawback: significant extra development effort to build wrappers and ensure smooth interoperation
+     - Still worth it if company’s life depends on system