# # Specify Texture

+   - glTexImage2D(target, level, internalformat, width, height, border, format, type, *texels);
+   - E.g.:
+     - target: GL_TEXTURE_2D
+     - Level : 0 (for no mip maps)
+     - Internalformat: GL_RGB
+     - Width,height: 2^m+2*b, 256 by 256 with b=0
+     - Border b: 0
+     - Format: GL_RGB
+     - Type: GL_INT
+     - texels: actual texture image