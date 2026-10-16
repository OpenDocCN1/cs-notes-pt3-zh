# 模板方法模式

模式应用

+   • OnDraw被定义为纯虚函数，在App Wizard生成代码框架时，为CView的派生类类自动生成了OnDraw函数。用户只需在CView派生类中的OnDraw函数中编写代码就可实现数据的正确显示，而不必关心OnDraw如何被调用。

+   • OnPrepareDC函数可用于在View中显示数据前修改设备上下文，或者打印时对打印机进行控制等。MFC CView对OnPrepareDC提供了默认实现，必要时，可以在派生类中覆盖该函数，实现用户特定的功能。

![](bbox=[0.65, 0.65, 0.95, 0.95])