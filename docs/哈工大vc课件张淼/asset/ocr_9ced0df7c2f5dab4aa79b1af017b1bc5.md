窗口函数的一般形式如下：

```
LRESULT CALLBACK WndProc(HWND hwnd, UINT messgae, WPARAM wParam, LPARAM lParam)
{
...
}
```

```
switch(message) // message为标识的消息
{ case ...
...
break;
...
```

在消息处理程序段中一般都有对WM_DESTROY的处理,该消息是关闭窗口时发出的。它向应用程序发出WM_QUIT消息,请求退出处理函数:
void PostQuitMessage(int nExitCode)
//nExitCode为应用程序的退出代码

```
case WM_DESTROY:
PostQuitMessage(0);
default:
return DefWindowProc(hwnd, message, wParam, lParam);
}
```

```
return(0);
}
```

为未定义处理过程的消息提供缺省处理