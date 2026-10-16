# 只有一句话： mov pos

PC/AT机内存区域图

0xffffffff
ROM BIOS
0x100000
……
VGA ROM BIOS
0xC0000
显存
0xA0000
0x00000

完成显示中最核心的秘密就是

mov pos, c

pos指向显存: pos=0xA0000

```
con_init();
```

```
void con_init(void)
{ gotoxy(ORIG_X,ORIG_Y); }
```

```
static inline void gotoxy()
{pos=origin+y*video_size_row +(x<<1);}
```

```
#define ORIG_X (*(unsigned char*)0x90000) //初始光标列号
#define ORIG_Y (*(unsigned char*)0x90001) //初始光标行号
```