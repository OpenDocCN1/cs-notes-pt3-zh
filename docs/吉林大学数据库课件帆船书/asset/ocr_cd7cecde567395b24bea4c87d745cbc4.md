# Attributes vs. Subelements

+   - Distinction between subelement and attribute
+     - In the context of documents, attributes are part of markup, while subelement contents are part of the basic document contents
+     - In the context of data representation, the difference is unclear and may be confusing
+       - Same information can be represented in two ways
+         - `<course course_id="CS-101">...</course>`
+         - `<course>
+           <course_id>CS-101</course_id>...
+           </course>`
+     - Suggestion: use attributes for identifiers of elements, and use subelements for contents

![](bbox=[0.0, 0.04, 0.09, 0.14])