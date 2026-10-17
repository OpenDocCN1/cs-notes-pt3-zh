# OpenGl Bezier-Spline Surface

1: specify parameters and active the routines for Bezier-curve display with the OpenGL functions:

+   - `glMap2*(GL_MAP2_*, uMin, uMax, ustride, unPts, vMin, vMax, vstride, vnPts, *ctrlP);`
+   - `glEnable(GL_MAP2_*);`

2: A coordinate position along the curve path is calculated with:

+   - `glEvalCoord2f(nvalue);`

```
GLfloat ctrlpoints[4][4][3] = {...}
glMap2f(GL_MAP2_VERTEX_3, 0, 1, 3, 4,
        0, 1, 12, 4, &ctrlpoints[0][0][0]);
glEnable(GL_MAP2_VERTEX_3);
for (j = 0; j <= 8; j++)
{
    glBegin (GL_LINE_STRIP);
        for (i = 0; i <= 30; i++)
            glEvalCoord2f((GLfloat)i/30.0, (GLfloat)j/8.0);
    glEnd();
    glBegin (GL_LINE_STRIP);
        for (i = 0; i <= 30; i++)
            glEvalCoord2f((GLfloat)j/8.0, (GLfloat)i/30.0)
    glEnd();
}
```

![](bbox=[0.685, 0.392, 0.949, 0.896])