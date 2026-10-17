# Creating a List

```
`void glNewList (GLuint list, GLenum mode);`
```

Specifies the start of a display list. OpenGL routines that are called subsequently are stored in a display list, except for a few restricted OpenGL routines that can't be stored.

Mode can be GL_COMPILE or GL_COMPILE_AND_EXECUTE.

```
`void glEndList (void);`
```

Marks the end of a display list.