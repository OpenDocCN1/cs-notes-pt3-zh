# 6.5.1.7 工作集模型(working set model)

工作集(working set): 进程在一段时间内所访问页面的集合。

...2 6 1 5 7 7 7 7 5 1 6 2 2 1 2 3 ... (page reference)

WS(t,Δ)={5,7,1,6,2}

Δ: 称为窗口尺寸(window size)。

Denning 认为：为使程序有效运行，工作集应能放入内存。