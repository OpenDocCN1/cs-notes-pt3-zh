
## OpenGL Texture mapping (Ref: Red book)

- Create texture objects
  - 1D, 2D, 3D
  - Specify what does texture contain: say, color, depth, etc.
- Specify how the texture is applied
  - Replace, modulate, or blend
- Enable texture mapping
- Specify scene with both geometric coordinates as well as texture coordinates

## Specify Texture

- glTexImage2D(target, level, internalformat, width, height, border, format, type, *texels);
- E.g.:
  - target: GL_TEXTURE_2D
  - Level : 0 (for no mip maps)
  - Internalformat: GL_RGB
  - Width,height: 2^m+2*b, 256 by 256 with b=0
  - Border b: 0
  - Format: GL_RGB
  - Type: GL_INT
  - texels: actual texture image

## Specifying mipmaps

- You need to specify the levels for which mipmapping is being used.
- You can also specify scale factor (between the texture image and size of polygon).
- You also need to supply images for all levels.
- You use glTexParameteri() and glTexImage2D()
  - `glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_BASE_LEVEL, 2);`
  - `glTexImage2D(...,2,...);`

## Automatic mipmap generation

- If you have highest resolution image, OpenGL can generate low level prefiltered images automatically.
- gluBuild2DMipmaps()
- gluBuild2DMipmapsLevels()
  - To build only a subset
- See book for detailed description of parameters

## OpenGL filtering

- We can specify the kind of filter to be applied
- OpenGL filtering is crude but fast
- Specify filter using glParameteri() with
  GL_TEXTURE_MAG_FILTER and GL_TEXTURE_MIN_FILTER
- E.g. filters : GL_NEAREST, GL_LINEAR,
  GL_NEAREST_MIPMAP_LINEAR (for minification)
- E.g.
  glParameteri(GL_TEXTURE_2D,GL_TEXTURE_MAG_FILTER,GL_NEAREST);

## Other calls

- glGenTextures();
  - To generate unique names
- glBindTexture();
  - Creates if texture object not already created
  - Activates the texture object if already created
  - Pass 0 to stop using texture objects
- glEnable(GL_TEXTURE_2D);
  - Enables texture mapping
- glTexCoord2i(texcoordinate);

## Tricks with Textures

- If the texture is not large enough to cover a polygon, you can tile it using the GL_REPEAT parameter
  - glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT );
- You can also clamp the texture (i.e., stretch the last pixel to cover everything)

## Boundaries

- You can control what happens if a point maps to a texture coordinate outside of the texture image
  – All textures are assumed to go from (0,0) to (1,1) in texture space
- Repeat: Assume the texture is tiled
  – glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT)
- Clamp: Clamp to Edge: the texture coordinates are truncated to valid values, and then used
  – glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP)
- Can specify a special border color:
  – glTexParameterfv(GL_TEXTURE_2D, GL_TEXTURE_BORDER_COLOR, R,G,B,A)

## Repeat Border

![](img/94fd648dd12ff5c2cbed197b5038ba1a_583_0.png)

## Clamp Border

![](img/94fd648dd12ff5c2cbed197b5038ba1a_584_0.png)

## Border Color

![](img/94fd648dd12ff5c2cbed197b5038ba1a_585_0.png)

## Yet More Texture Stuff

- There is a 4x4 texture matrix: apply a matrix transformation to texture coordinates before indexing texture
- There are “image processing” operations that can be applied to the pixels coming out of the texture

## Environment Mapping

- Environment mapping produces reflections on shiny objects
- Texture is transferred in the direction of the reflected ray from the environment map onto the object
- Reflected ray: $R=2(N\cdot V)N-V$

![](img/94fd648dd12ff5c2cbed197b5038ba1a_588_0.png)
