# 串的块链的类型定义

```
#define CHUNKSIZE 80
typedef struct Chunk{
    char ch[CHUNKSIZE];
    struct Chunk *next;
}Chunk;
```

```
Typedef struct{
    Chunk *head,*tail;
    int curlen;
}LString;
```