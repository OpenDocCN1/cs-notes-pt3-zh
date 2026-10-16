```
Status CopyGList(Glist &T, Glist L) {
    if (!L) T = NULL; // 复制空表
    else {
        if (!(T = (Glist)malloc(sizeof(GLNode))))
            exit(OVERFLOW); // 建表结点
        T->tag = L->tag;
        if (L->tag == ATOM)
            T->data = L->data; // 复制单原子结点
        else { 分别复制表头和表尾 }
    } // else
    return OK;
} // CopyGList
```