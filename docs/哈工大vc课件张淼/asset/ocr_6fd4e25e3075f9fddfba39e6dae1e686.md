# 创建窗口 — 第三步

# 创建窗口实例— CreateWindow

```
HWND CreateWindow (
LPCTSTR lpszClassName, //窗口类名
LPCTSTR lpszTitle,    //窗口标题名
DWORD dwStyle,        //创建窗口的样式
int x,y,              //窗口左上角坐标
int nWidth,nHeight,   //窗口宽度和高度
HWND hwndParent,      //该窗口的父窗口句柄
HMENU hMenu,          //窗口主菜单句柄
HINSTANCE hInstance, //创建窗口的应用程序当前句柄
LPVOID lpParam        //指向一个传递给窗口的参数值的指针
)
```