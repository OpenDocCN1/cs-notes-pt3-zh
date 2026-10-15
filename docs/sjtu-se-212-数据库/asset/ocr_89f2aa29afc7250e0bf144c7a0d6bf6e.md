# Composite and Multivalued Attributes

![](bbox=[0.032, 0.115, 0.308, 0.698])

+   - Composite attributes are flattened out by creating a separate attribute for each component attribute
+     - Example: given entity set `instructor` with composite attribute `name` with component attributes `first_name` and `last_name`, the schema corresponding to the entity set has two attributes `name_first_name` and `name_last_name`
+       - Prefix omitted if there is no ambiguity
+   - Ignoring multivalued attributes, extended instructor schema is
+     - `instructor(ID, first_name, middle_initial, last_name, street_number, street_name, apt_number, city, state, zip_code, date_of_birth)`