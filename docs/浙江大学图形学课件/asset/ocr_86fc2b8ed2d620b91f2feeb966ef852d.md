# # Mouse (cont)

```
glGetIntegerv (GL_VIEWPORT, viewport);

glSelectBuffer (SIZE, selectBuf);
glRenderMode(GL_SELECT);

glInitNames();
glPushName(0);

glMatrixMode (GL_PROJECTION);
glPushMatrix ();
glLoadIdentity ();
/* create 5x5 pixel picking region near cursor location */
gluPickMatrix ((GLdouble) x, (GLdouble) (viewport[3] - y),
5.0, 5.0, viewport);
gluOrtho2D (-2.0, 2.0, -2.0, 2.0);
drawObjects(GL_SELECT);

glMatrixMode (GL_PROJECTION);
glPopMatrix ();
glFlush ();
hits = glRenderMode (GL_RENDER);
processHits (hits, selectBuf);
glutPostRedisplay();
```