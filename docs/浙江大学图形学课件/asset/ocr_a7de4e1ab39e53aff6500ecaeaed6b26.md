# # Mipmapping

+   - Like any other object, a texture mapped object can be viewed from many distances.
+   - Sometimes, that causes problems.
+     - A low-resolution texture (say, 32x32) applied to a big polygon (say, one that occupies a 512x512 area on screen) will appear blocky.
+     - Conversely, if you apply a high-resolution texture to a small polygon, how do you decide which texels to show and which to ignore?