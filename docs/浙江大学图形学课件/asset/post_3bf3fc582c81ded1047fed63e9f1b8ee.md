

## Examples

GLfloat list[6][2] ;
glBegin(GL_LINES)
for (int i = 0 ; i < 6 ;i++)
glVertex2v(list[i]);
glEnd() ;
glBegin(GL_LINE_STRIP)
for (int i = 0 ; i < 6 ;i++)
glVertex2v(list[i]);
glEnd() ;
glBegin(GL_LINE_LOOP)
for (int i = 0 ; i < 6 ;i++)
glVertex2v(list[i]);
glEnd() ;

![](img/94fd648dd12ff5c2cbed197b5038ba1a_112_0.png)

## Examples

```
GLfloat list[6][2] ;

glColor3f(0.0, 1.0, 0.0);
glBegin(GL_TRIANGLES)
    for (int i = 0 ; i < 6 ; i++)
        glVertex2v(list[i]);
glEnd() ;

glBegin(GL_TRIANGLES)
    glColor3f(1.0, 0.0, 0.0);
    for ( i = 0 ; i < 3 ; i++)
        glVertex2v(list[i]);
    glColor3f(1.0, 1.0, 1.0);
    for ( i = 3 ; i < 6 ; i++)
        glVertex2v(list[i]);
glEnd() ;
```

![](img/94fd648dd12ff5c2cbed197b5038ba1a_113_0.png)

## Examples

GL_TRIANGLE_STRIP

GL_TRIANGLE_FAN

GL_QUAD_STRIP

P1 P3 P5 P6 P0 P2 P4 P7

Must be planar convex

![](img/94fd648dd12ff5c2cbed197b5038ba1a_114_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_114_1.png)

## glVertex

- All primitives are defined in terms of vertices
  - `glVertex2f( x, y );`
  - `glVertex3f( x, y, z );`
  - `glVertex4f( x, y, z, w );`
  - `glVertex3fv( a );`  // with a[0], a[1], a[2]

## Building Objects From Vertices

- Specify a primitive mode, and enclose a set of vertices in a glBegin / glEnd block
  ```
  glBegin( GL_POLYGON );
  glVertex3f( 1.0, 2.0, 0.0 );
  glVertex3f( 0.0, 0.0, 0.0 );
  glVertex3f( 3.0, 0.0, 0.0 );
  glVertex3f( 3.0, 2.0, 0.0 );
  glEnd();
  ```

## OpenGL Example

```c
void drawOneCubeface(size)
{
    static GLfloat v[8][3];
    v[0][0] = v[3][0] = v[4][0] = v[7][0] = -size/2.0;
    v[1][0] = v[2][0] = v[5][0] = v[6][0] = size/2.0;
    v[0][1] = v[1][1] = v[4][1] = v[5][1] = -size/2.0;
    v[2][1] = v[3][1] = v[6][1] = v[7][1] = size/2.0;
    v[0][2] = v[1][2] = v[2][2] = v[3][2] = -size/2.0;
    v[4][2] = v[5][2] = v[6][2] = v[7][2] = size/2.0;
    glBegin( GL_POLYGON );
        glVertex3fv(v[0]);
        glVertex2fv(v[1]);
        glVertex2fv(v[2]);
        glVertex2fv(v[3]);
    glEnd();
}
```

![](img/94fd648dd12ff5c2cbed197b5038ba1a_118_0.png)

## Colors

- OpenGL colors are typically defined as RGB components, each of which is a float in the range [0.0, 1.0]
- For the screen’s background:
  glClearColor( 0.0, 0.0, 0.0 ); // black color
  glClear( GL_COLOR_BUFFER_BIT );
- For objects:
  glColor3f( 1.0, 1.0, 1.0 ); // white color

## Other Commands in glBegin / glEnd blocks

- Not every OpenGL command can be located in such a block. Those that can include, among others:
  - glColor
  - glNormal (to define a normal vector)
  - glTexCoord (to define texture coordinates)
  - glMaterial (to set material properties)

## Example

```
glBegin( GL_POLYGON );
    glColor3f( 1.0, 1.0, 0.0 );
    glVertex3f( 0.0, 0.0, 0.0 );
    glColor3f( 0.0, 1.0, 1.0 );
    glVertex3f( 5.0, 0.0, 0.0 );
    glColor3f( 1.0, 0.0, 1.0 );
    glVertex3f( 0.0, 5.0, 0.0 );
glEnd();
```

## Polygon Display Modes

- `glPolygonMode( GLenum face, GLenum mode );`  
  Faces: `GL_FRONT`, `GL_BACK`, `GL_FRONT_AND_BACK`  
  Modes: `GL_FILL`, `GL_LINE`, `GL_POINT`  
  By default, both the front and back face are drawn filled
- `glFrontFace( GLenum mode );`  
  Mode is either `GL_CCW` (default) or `GL_CW`
- `glCullFace( GLenum mode );`  
  Mode is either `GL_FRONT`, `GL_BACK`, `GL_FRONT_AND_BACK`;
- You must enable and disable culling with `glEnable( GL_CULL_FACE )` or `glDisable( GL_CULL_FACE );`

## Drawing Other Objects

- GLU contains calls to draw cylinders, cones and more complex surfaces called NURBS
- GLUT contains calls to draw spheres and cubes

## Compiling OpenGL Programs

- To use GLUT:
  - `#include <GL/glut.h>`
  - This takes care of every other include you need
  - Make sure that glut.lib (or glut32.lib) is in your compiler’s library directory, and that the object module or DLL is also available
- See *OpenGL Game Programming* or online tutorials for details.

