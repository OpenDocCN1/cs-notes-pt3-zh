# 获取设备描述表：方法一

+   □ 该方法适合于处理非WM_PAINT消息

+   ■ 用GetDC获取设备描述表句柄

+   ■ 用ReleaseDC释放设备描述表句柄

+   □ 这种获取设备描述表的一般方式如下

```
hdc = GetDC(hwnd) ;
......
ReleaseDC(hwnd, hdc) ;
```