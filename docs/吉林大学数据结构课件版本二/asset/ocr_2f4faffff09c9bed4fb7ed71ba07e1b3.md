# 求队列的长度

+   - int Queuelength(SqQueue Q)
+   - {
+   - return(Q.rear-Q.front+MAXQSIZE)%
+   - MAXQSIZE;
+   - }