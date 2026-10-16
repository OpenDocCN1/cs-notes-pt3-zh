# 典型用法

```
/* 库函数 memcpy的声明 */
void *memcpy(void *dest, void *src, size_t n);
```

```
/*内核内存区域保持用户访问数据*/
#define KSIZE 1024
char kbuf[KSIZE];

/* 从内核内存区域最多拷贝maxlen字节到用户缓冲区*/
int copy_from_kernel(void *user_dest, int maxlen) {
    /*字节数len=min（缓冲区大小,maxlen） */
    int len = KSIZE < maxlen ? KSIZE : maxlen;
    memcpy(user_dest, kbuf, len);
    return len;
}
```

```
#define MSIZE 528
void getstuff() {
    char mybuf[MSIZE];
    copy_from_kernel(mybuf, MSIZE);
    printf("%s\n", mybuf);
}
```