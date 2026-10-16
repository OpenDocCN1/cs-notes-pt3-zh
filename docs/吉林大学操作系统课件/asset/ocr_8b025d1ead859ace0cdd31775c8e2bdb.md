# 块型设备控制结构

```
struct devtab
{
char d_active;    /* busy flag */
char d_ercnt;    /* error count */
struct buf *b_forw;    /* first buffer for this dev */
struct buf *b_back;    /* last buffer for this dev */
struct buf *d_actf;    /* head of IO queue */
struct buf *d_actl;    /* tail of IO queue */
}
```