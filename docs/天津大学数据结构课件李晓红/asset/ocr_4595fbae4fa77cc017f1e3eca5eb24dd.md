# Status GetHead(LinkQueue Q,QElemType &e)

+   - `{ // 若队列不空,则用e返回Q的队头元素,并返回OK,否则返回ERROR`
+   - `QueuePtr p;`
+   - `if(Q.front==Q.rear)`
+   - `return ERROR;`
+   - `p=Q.front->next;`
+   - `e=p->data;`
+   - `return OK;`
+   - `}`