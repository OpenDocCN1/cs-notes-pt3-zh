# # Graphical User Interfaces (2)

```
while (running) {
    XNextEvent(disp, &event);      /* get next event */
    switch (event.type) {
    case Expose:   ...; break;     /* repaint window */
    case ButtonPress: ...; break;  /* process mouse click */
    case Keypress:  ...; break;    /* process keyboard input */
    }
}
XFreeGC(disp, gc);                 /* release graphic context */
XDestroyWindow(disp, win);         /* deallocate window's memory space */
XCloseDisplay(disp);               /* tear down network connection */
}
```

Figure 5-38. A skeleton of an X Window application program.