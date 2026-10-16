# 获取设备描述表：方法三

+   □ 获取整个窗口的设备描述表
+     ■ 用GetWindowDC获取整个窗口的设备描述表句柄
+     ■ 用ReleaseDC释放设备描述表句柄

```
HDC hdc;

Hdc = GetWindowDC(hWnd);
//使用设备描述表
.....

ReleaseDC(hWnd,hdc);
```