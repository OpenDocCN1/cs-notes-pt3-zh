
# IDE Specification

- Xv6 uses a relative old IDE specification
  - Not PCI negotiation
- IDE Ports
  - 0x1F0-0x1F7
    - 0x1f0: write/read port
    - 0x1f2: number of sectors
    - 0x1f3-0x1f5: sector number
    - 0x1f6: diskno and sector number
    - 0x1f7: command registers, status bit
  - 0x3F6 interrupt control line

# Polling Mechanism

```
32 // Wait for IDE disk to become ready.
33 static int
34 idewait(int checkerr)
35 {
36     int r;
37
38     while(((r = inb(0x1f7)) & (IDE_BSY|IDE_DRDY)) != IDE_DRDY)
39     ;
40     if(checkerr && (r & (IDE_DF|IDE_ERR)) != 0)
41         return -1;
42     return 0;
43 }
```

# IDE Initialization

```c
void
ideinit(void)
{
    int i;

    initlock(&idelock, "ide");
    picenable(IRQ_IDE);
    iopicenable(IRQ_IDE, ncpu - 1);
    idewait(0);

    // Check if disk 1 is present
    outb(0x1f6, 0xe0 | (1<<4));
    for(i=0; i<1000; i++){
        if(inb(0x1f7) != 0){
            havedisk1 = 1;
            break;
        }
    }

    // Switch back to disk 0.
    outb(0x1f6, 0xe0 | (0<<4));
}
```

# Synchronous I/O
(iderw)

```
122 // Sync buf with disk.
123 // If B_DIRTY is set, write buf to disk, clear B_DIRTY, set B_VALID.
124 // Else if B_VALID is not set, read buf from disk, set B_VALID.
125 void
126 iderw(struct buf *b)
127 {
128
129     struct buf **pp;
130
131     if(!(b->flags & B_BUSY))
132         panic("iderw: buf not busy");
133     if((b->flags & (B_VALID|B_DIRTY)) == B_VALID)
134         panic("iderw: nothing to do");
135     if(b->dev != 0 && !havedisk1)
136         panic("iderw: ide disk 1 not present");
137
138     acquire(&idelock);  //DOC:acquire-lock
139
140     // Append b to idequeue.
141     b->qnext = 0;
142     for(pp=&idequeue; *pp; pp=&(*pp)->qnext)  //DOC:insert-queue
143         ;
144     *pp = b;
145
146     // Start disk if necessary.
147     if(idequeue == b)
148         idestart(b);
149
150     // Wait for request to finish.
151     while((b->flags & (B_VALID|B_DIRTY)) != B_VALID){
152         sleep(b, &idelock);
153     }
154
155     release(&idelock);
156 }
```

```c
// Atomically release lock and sleep on chan.
// Requires lock when awakened.
void
sleep(void *chan, struct spinlock *lk)
{
  if(proc == 0)
    panic("sleep");

  if(lk == 0)
    panic("sleep without lk");

  // Must acquire ptable.lock in order to
  // change p->state and then call sched.
  // Once we hold ptable.lock, we can be
  // guaranteed that we won't miss any wakeup
  // (wakeup runs with ptable.lock locked),
  // so it's okay to release lk.
  if(lk != &ptable.lock){  //DOC: sleeplock0
    acquire(&ptable.lock);  //DOC: sleeplock1
    release(lk);
  }

  // Go to sleep.
  proc->chan = chan;
  proc->state = SLEEPING;
  sched();

  // Tidy up.
  proc->chan = 0;

  // Reacquire original lock.
  if(lk != &ptable.lock){  //DOC: sleeplock2
    release(&ptable.lock);
    acquire(lk);
  }
}
```

```c
// Wake up all processes sleeping on chan.
// The ptable lock must be held.
static void
wakeup1(void *chan)
{
  struct proc *p;

  for(p = ptable.proc; p < &ptable.proc[NPROC]; p++)
    if(p->state == SLEEPING && p->chan == chan)
      p->state = RUNNABLE;
}

// Wake up all processes sleeping on chan.
void
wakeup(void *chan)
{
  acquire(&ptable.lock);
  wakeup1(chan);
  release(&ptable.lock);
}
```

# Sleep and Wakeup Mechanism in xv6

```
68 // Start the request for b. Caller must hold idelock.
69 static void
70 idestart(struct buf *b)
71 {
72     if(b == 0)
73         panic("idestart");
74
75     idewait(0);
76     outb(0x3f6, 0);  // generate interrupt
77     outb(0x1f2, 1);  // number of sectors
78     outb(0x1f3, b->sector & 0xff);
79     outb(0x1f4, (b->sector >> 8) & 0xff);
80     outb(0x1f5, (b->sector >> 16) & 0xff);
81     outb(0x1f6, 0xe0 | ((b->dev&1)<<4) | ((b->sector>>24)&0x0f));
82     if(b->flags & B_DIRTY){
83         outb(0x1f7, IDE_CMD_WRITE);
84         outsl(0x1f0, b->data, 512/4);
85     } else {
86         outb(0x1f7, IDE_CMD_READ);
87     }
88 }
```
