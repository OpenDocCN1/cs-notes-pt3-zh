# Mapping XML Data to Relations

+   - Relation created for each element type whose schema is known:
+     - An id attribute to store a unique id for each element
+     - A relation attribute corresponding to each element attribute
+     - A parent_id attribute to keep track of parent element
+       - As in the tree representation
+       - Position information (i<sup>th</sup> child) can be store too
+   - All subelements that occur only once can become relation attributes
+     - For text-valued subelements, store the text as attribute value
+     - For complex subelements, can store the id of the subelement
+   - Subelements that can occur multiple times represented in a separate table
+     - Similar to handling of multivalued attributes when converting ER diagrams to tables