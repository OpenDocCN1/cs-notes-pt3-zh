# MFC对象和Windows对象

Windows 窗口在MFC窗口对象创建之后，由 CWnd 类的 Create 成员函数创建， “窗口句柄” 保存存在窗口对象的 m_hWnd 成员变量中。Windows 窗口可以被一个程序销毁，也可以被用户的动作销毁。