```
linklist connect(linklist reara,linklist &rearb)
{
    linklist p=reara->next;
    reara->next=(rearb->next)->next;
    free(rearb->next);
    rearb->next=p;
    return(rearb);
}
```