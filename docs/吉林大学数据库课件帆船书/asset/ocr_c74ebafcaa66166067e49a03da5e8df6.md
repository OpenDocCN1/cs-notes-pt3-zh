# Materialized Views

+   - **Materializing a view**: create a physical table containing all the tuples in the result of the query defining the view
+   - If relations used in the query are updated, the materialized view result becomes out of date
+     - Need to **maintain** the view, by updating the view whenever the underlying relations are updated.