# PAINTSTRUCT结构

+   - Windows系统为每一个窗口建立了一个PAINTSTRUCT结构。该结构中包含了包围无效区域的一个最小矩形的结构RECT，应用程序可以根据这个无效区域执行更新的操作。PAINTSTRUCT结构体不需要我们维护，是系统内部维护的结构体。