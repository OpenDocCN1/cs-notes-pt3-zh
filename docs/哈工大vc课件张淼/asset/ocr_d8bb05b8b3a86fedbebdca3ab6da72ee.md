# Windows系统

# 排队消息

+   WM_KEYDOWN
+   WM_KEYUP
+   WM_MOUSEMOVE
+   WM_LBUTTONDOWN
+   WM_QUIT
+   ...

# 非排队消息

+   WM_CREATE
+   WM_DESTROY
+   WM_SIZE
+   WM_PAINT
+   ...

应用程序的消息队列

检索到的消息

GetMessage ()

WinMain ()

消息循环

DispatchMessage ()

应用程序

回调

WndProc ()

+   case 1
+   case 2
+   case 3
+   ...
+   Default

DefWindowProc ()