# 创建窗口 — 第一步

# 窗口类的定义 — WNDCLASS

```
typedef struct tagWNDCLASS{
    UINT style;                 //窗口类风格
    WNDPROC lpfnWndProc;        //窗口过程函数
    int cbClsExtra;             //在类结构中预留的空间
    int cbWndExtra;             //在Windows内部预留空间
    HINSTANCE hInstance;        //程序实例句柄
    HICON hIcon;                //窗口的图标
    HCURSOR hCursor;            //光标句柄
    HBRUSH hbrBackground;       //背景色
    LPCTSTR lpszMenuName;       //窗口类菜单
    LPCTSTR lpszClassName;      //窗口类名
} WNDCLASS, *PWNDCLASS;
```