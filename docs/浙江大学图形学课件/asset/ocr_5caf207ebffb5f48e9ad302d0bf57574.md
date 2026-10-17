# Step 3: Dereferencing & Rendering

+   - (2). Dereference a List of Array Elements
+     - `void glDrawElements(GLenum mode, GLsizei count, GLenum type, void *indices);`
+       - Defines a sequence of geometric primitives using count number of elements, whose indices are stored in the array indices. type must be one of GL_UNSIGNED_BYTE, GL_UNSIGNED_SHORT, or GL_UNSIGNED_INT, indicating the data type of the indices array.
+       - mode specifies what kind of primitives are constructed and is one of the same values that is accepted by `glBegin()`;
+         - for example, GL_POLYGON, GL_LINE_LOOP, GL_LINES, GL_POINTS, and so on.