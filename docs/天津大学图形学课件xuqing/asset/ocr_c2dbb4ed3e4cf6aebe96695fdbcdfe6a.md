# # Control Functions

+   - void auxMainLoop(void(*displayFunc)void)
+     -Windows message: WM_PAINT

+   - void auxReshapeFunc(void(*function)
+     (GLsizei,Glsizei))
+     -Windows message: WM_SIZE

+   - void auxMouseFunc(Glint button,Glint mode,
+     void(*function)(AUX_EVENTREC*))
+     -Windows Message: WM_MOUSEDOWN