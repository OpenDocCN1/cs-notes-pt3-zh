# # Cube Mapping

+   - The map resides on the surfaces of a cube around the object
+     - Typically, align the faces of the cube with the coordinate axes
+   - To generate the map:
+     - For each face of the cube, render the world from the center of the object with the cube face as the image plane
+       - Rendering can be arbitrarily complex (it’s off-line)
+     - Or, take 6 photos of a real environment with a camera in the object’s position
+   - Assume the cube’s faces are aligned with the coordinate axes, and have texture coordinates in [0,1]x[0,1]. Main issue is to decide
+     - which face to use, and
+     - decide which texture coordinates to use.
+     - Use a ray from the centre; only cube corners and edges will need special attention