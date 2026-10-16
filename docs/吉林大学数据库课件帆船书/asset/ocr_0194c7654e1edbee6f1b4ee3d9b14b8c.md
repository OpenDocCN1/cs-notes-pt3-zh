# Authorization on Views

+   - **create view** *geo_instructor* **as**
+     (**select** *
+     **from** *instructor*
+     **where** *dept_name* = 'Geology');
+   - **grant select on** *geo_instructor* **to** *geo_staff*
+   - Suppose that a *geo_staff* member issues
+     - **select** *
+       **from** *geo_instructor*,
+   - What if
+     - *geo_staff* does not have permissions on *instructor*?
+     - creator of view did not have some permissions on *instructor*?