
## while(i<entries)...

```
while(i<entries) //entries是目录项数
{ if((char*)de >= BLOCK_SIZE+bh->b_size
    brelse(bh);
    block=bmap(*dir,i/DIR_ENTRIES_PER_BLOCK);
    bh=bread((*dir)->i_dev,block);
    de=(struct dir_entry*)bh->b_data;
} //读入下一块上的目录项继续match
if(match(namelen,name,de))
{*res_dir=de;return bh;}
de++; i++; }
```

> #define BLOCK_SIZE 1024 //两个扇区

![](img/365fc74cce32b405409a65a7e8830bec_373_0.png)

## 操作系统全图

![](img/365fc74cce32b405409a65a7e8830bec_374_0.png)

![](img/365fc74cce32b405409a65a7e8830bec_374_1.png)
