# MFC框架的基本类

# CFrameWnd

+   - 应用程序框架窗口类
+   - 负责显示交互界面，包括菜单和工具栏等
+   - 对于单文档应用程序，其基类为 CFrameWnd；对于多文档应用程序，其主窗口基类为CMDIFrameWnd，每一个视图的主窗口基类为CMD IChildWnd
+   - 对于SDI程序，窗口框架命名为 CMainFrame；对于MDI应用程序，主框架窗口命名为CMainFrame，子窗口命名为 CChildFrame