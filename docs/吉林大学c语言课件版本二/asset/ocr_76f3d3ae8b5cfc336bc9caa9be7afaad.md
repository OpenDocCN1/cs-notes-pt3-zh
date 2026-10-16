# 12.2

| 循环 | 递归 |
|---|---|
| ```c
int len(struct tr *x){
    int L=0;
    struct tr *tp=x;
    while(tp!=NULL){
        L++;
        tp=tp->n;
    }
    return L;
}
``` | ```c
int len(struct tr *x){
    if(x==NULL)
        return 0;
    else
        return len(x->n)+1;
}
``` |