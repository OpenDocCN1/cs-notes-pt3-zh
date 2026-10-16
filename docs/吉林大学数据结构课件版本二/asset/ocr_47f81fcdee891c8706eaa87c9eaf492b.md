```
result searchbtree(BTree T,KeyType K)
{
    P=T; q=NULL; found=FALSE; i=0;
    While(p&& !found)
    {
        i=search(p,K);
        if(i>0&&p->key[i]==K) found=TRUE;
        else {q=p;p=p->ptr[i];}
    }
    if(found) return(p,i,1);
    else return(q,i,0);
}
```