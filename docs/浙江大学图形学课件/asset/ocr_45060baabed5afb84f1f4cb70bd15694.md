# Tricks with Textures

+   - If the texture is not large enough to cover a polygon, you can tile it using the GL_REPEAT parameter
+     - glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT );
+   - You can also clamp the texture (i.e., stretch the last pixel to cover everything)