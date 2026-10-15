# 3. Given a stack ADT, explain how can use it to implement a queue ADT.

+   - Use two stack instance to implement queue.
+   - When enque, always push to first stack.
+   - When deque, if the second stack is empty, pop all element from first stack and push them into the second stack. When the second stack is not empty, pop one element from second stack and return.