+   - 若得到是上述3个文件，须手动拷贝到相应目录下：
+     - glut32.dll文件复制到Windows的系统目录下（Win9X是system目录，其它是system32目录）。
+     - glut32.lib文件复制到VC的lib目录下，glut.h复制到VC的include\\GL目录下。
+   - 在Visual C++中创建一个空的Win32的控制台应用程序；在Project/Settings对话框中的Link选项卡中的Object/library modules一栏中加入opengl32.lib、glu32.lib和glut32.lib。
+   - 接下来就可加入新的源文件进行编程调试了。