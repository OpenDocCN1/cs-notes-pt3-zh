# # Texture Matrix

+   - Loading a texture onto the graphics card is very expensive
+   - But once there, a **texture matrix** can be used to “transform” the texture
+     - For example, changing the translation can select different parts of the texture
+   - If the texture matrix is changed from frame to frame, the texture will appear to move on the object
+   - This is particularly useful for things like flame, or swirling vortices, …