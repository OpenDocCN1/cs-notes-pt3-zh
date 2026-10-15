```
122 // Sync buf with disk.
123 // If B_DIRTY is set, write buf to disk, clear B_DIRTY, set B_VALID.
124 // Else if B_VALID is not set, read buf from disk, set B_VALID.
125 void
126 iderw(struct buf *b)
127 {
128     struct buf **pp;
129
130     if(!(b->flags & B_BUSY))
131         panic("iderw: buf not busy");
132     if((b->flags & (B_VALID|B_DIRTY)) == B_VALID)
133         panic("iderw: nothing to do");
134     if(b->dev != 0 && !havedisk1)
135         panic("iderw: ide disk 1 not present");
136
137     acquire(&idelock);  //DOC:acquire-lock
138
139     // Append b to idequeue.
140     b->qnext = 0;
141     for(pp=&idequeue; *pp; pp=&(*pp)->qnext)  //DOC:insert-queue
142         ;
143     *pp = b;
144
145     // Start disk if necessary.
146     if(idequeue == b)
147         idestart(b);
148
149     // Wait for request to finish.
150     while((b->flags & (B_VALID|B_DIRTY)) != B_VALID){
151         sleep(b, &idelock);
152     }
153
154     release(&idelock);
155 }
```

# Synchronous I/O
(iderw)