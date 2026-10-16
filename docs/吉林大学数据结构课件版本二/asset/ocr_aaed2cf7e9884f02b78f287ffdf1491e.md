```
void union(List &La, List Lb) {
    La_len=listlength(La);
    Lb_len=listlength(Lb);
    for(i=1;i<=Lb_len;i++) {
        GetElem(Lb, i, &e);
        if(!locateElem(La, e, qual))
            ListInsert(La, ++La_en, e);
    }
}
```

T(n)=O(listlength(La) *listlength(Lb))