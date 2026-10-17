# # Z-buffer enhanced for shadows

+   - Second step - the scene is rendered from the actual view with an enhanced z-buffer algorithm
+     - if a point (x, y, z) is visible, than the view transformation of the light source is applied to the point which maps it to a point (x¹, y¹, z¹)
+     - (x¹, y¹, z¹) is a view of the point (x, y, z) seen from the source
+     - (x¹, y¹) is used to index into the shadow z-buffer and the corresponding depth value is compared with z¹
+     - if z¹ is greater than the depth value then the (x, y, z) is in a shadow