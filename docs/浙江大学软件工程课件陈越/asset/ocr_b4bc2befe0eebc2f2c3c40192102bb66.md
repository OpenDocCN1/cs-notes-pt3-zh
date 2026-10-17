# # 第八章 指针和引用

☆在链表的表尾结点后插入一个新结点  
例： 将pNew所指的结点插到链表的表尾  
StudentNode*tail;  
tail=head;  
while(tail != NULL && tail→next != NULL)  
tail=tail→next;  
tail→next=pNew;