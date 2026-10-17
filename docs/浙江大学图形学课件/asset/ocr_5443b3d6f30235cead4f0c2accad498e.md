# # Editable Display Lists

+   • Example editable display list: To render the polygon, call display list number 4. To edit a vertex, you need only recreate the single display list corresponding to that vertex.

```
glNewList(1,GL_COMPILE);
glVertex3f(v1);
glEndList();
glNewList(2,GL_COMPILE);
glVertex3f(v2);
glEndList();
glNewList(3,GL_COMPILE);
glVertex3f(v3);
glEndList();
glNewList(4,GL_COMPILE);
glBegin(GL_POLYGON);
glCallList(1); glCallList(2); glCallList(3);
glEnd();
glEndList();
```