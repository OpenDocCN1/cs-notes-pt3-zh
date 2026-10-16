# 1、串的插入

```
status sinsert(Hstring &S,int pos,Hstring T)
{
    if(pos<1 || pos>S.length+1)    return error;
    if(T.length)
    {
        if(!(S.ch=(char*)realloc(S.ch,(S.length+T.length)*sizeof(char)))    exit(overflow);
        for(i=S.length-1;i>=pos-1;--i)S.ch[i+T.length]=S.ch[i]
        S.ch[pos-1..pos+T.length-2]= T.ch[0..T.length-1];
        S.length+=T.length;
    }
    return OK;
}
```