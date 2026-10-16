# Motivation for Nesting

![](bbox=[0.0, 0.0, 0.08, 0.12])

+   - Nesting of data is useful in data transfer
+     - Example: elements representing *item* nested within an *itemlist* element
+   - Nesting is not supported, or discouraged, in relational databases
+     - With multiple orders, customer name and address are stored redundantly
+     - normalization replaces nested structures in each order by foreign key into table storing customer name and address information
+     - Nesting is supported in object-relational databases
+   - But nesting is appropriate when transferring data
+     - External application does not have direct access to data referenced by a foreign key