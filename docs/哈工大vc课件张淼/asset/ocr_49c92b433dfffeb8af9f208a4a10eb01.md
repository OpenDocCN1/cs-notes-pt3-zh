# LoadIcon

LoadIcon的作用是在应用程序中加载一个窗口图标，其原型为：

```
HICON LoadIcon(
    HINSTANCE hInstance,
    LPCTSTR lpIconName
);
```

图标资源名或系统预定义图标标识名

图标资源所在的模块句柄，NULL则使用系统预定义图标