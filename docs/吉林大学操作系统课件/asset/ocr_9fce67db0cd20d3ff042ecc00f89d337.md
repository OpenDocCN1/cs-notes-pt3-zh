# 字符型设备缓冲

```
struct cblock {
    struct cblock *c_next;
    char info[6];
}

struct cblock *cfreelist;  //free c blocks

struct clist  //associated with a character device
{
    int c_cc;  //character count
    int c_cf;  //pointer to first block
    int c_cl;  //pointer to last block
}
```