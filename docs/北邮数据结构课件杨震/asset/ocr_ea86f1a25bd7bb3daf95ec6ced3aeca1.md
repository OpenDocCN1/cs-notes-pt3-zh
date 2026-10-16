# [例3]以下程序的功能是实现带附加头结点的单链表数据结构点逆序连接，请填空完善之。

```
typedef struct node
{int data; struct node *next;
}linknode,*pointer;
void reverse(pointer & h)//h为头指针
{ pointer p,q;
 p=h->next; h->next=NULL;
 while((1)__________)
 {
  q=p;
  p=p->next;
  q->next=h->next;
  h->next=(2)__________;
 }
}
```

(1)p!=null  // 链表未到尾就一直作
(2)q      // 将当前结点作为头结点后的第一元素结点插入