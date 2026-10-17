# # 线索二叉树 (Threaded Binary Tree)

# ## 结点结构

![](bbox=[0.121, 0.311, 0.861, 0.408])

+   - LeftChild
+   - LeftThread
+   - data
+   - RightThread
+   - RightChild

LeftThread=0, LeftChild为左子女指针  
LeftThread=1, LeftChild为前驱线索  
RightThread=0, RightChild为右子女指针  
RightThread=1, RightChild为后继指针