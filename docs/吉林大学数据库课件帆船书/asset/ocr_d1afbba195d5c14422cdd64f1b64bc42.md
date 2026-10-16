# Multivalued Dependencies

+   - Suppose we record names of children, and phone numbers for instructors:
+     - *inst_child(ID, child_name)*
+     - *inst_phone(ID, phone_number)*

+   - If we were to combine these schemas to get
+     - *inst_info(ID, child_name, phone_number)*
+     - Example data:
+       (99999, David, 512-555-1234)
+       (99999, David, 512-555-4321)
+       (99999, William, 512-555-1234)
+       (99999, William, 512-555-4321)

+   - This relation is in BCNF
+     - Why?