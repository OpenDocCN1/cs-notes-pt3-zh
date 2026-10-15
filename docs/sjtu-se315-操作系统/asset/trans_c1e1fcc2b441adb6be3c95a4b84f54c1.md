

```c
void spin_lock(spinlock_t *lock)
{
    t = atomic_inc(lock->next_ticket);
    while (t != lock->current_ticket)
        ; /* Spin */
}
```

```c
void spin_unlock(spinlock_t *lock)
{
    lock->current_ticket++;
}
```

```c
struct spinlock_t {
    int current_ticket;
    int next_ticket;
}
```

500 ~ 4000 cycles!

![](img/53ee1e3b0eba43505c7d530851f32f6f_788_0.png)

所有等待者读取锁

```c
void spin_lock(spinlock_t *lock)
{
    t = atomic_inc(lock->next_ticket);
    while (t != lock->current_ticket)
        ; /* Spin */
}
```

```c
void spin_unlock(spinlock_t *lock)
{
    lock->current_ticket++;
}
```

```c
struct spinlock_t {
    int current_ticket;
    int next_ticket;
}
```

逐一回复读请求

![](img/53ee1e3b0eba43505c7d530851f32f6f_789_0.png)

所有等待者读取锁

```c
void spin_lock(spinlock_t *lock)
{
    t = atomic_inc(lock->next_ticket);
    while (t != lock->current_ticket)
        ;  /* Spin */
}
```

```c
void spin_unlock(spinlock_t *lock)
{
    lock->current_ticket++;
}

struct spinlock_t {
    int current_ticket;
    int next_ticket;
}
```

逐一回复读请求

![](img/53ee1e3b0eba43505c7d530851f32f6f_790_0.png)

所有等待者读取锁

```c
void spin_lock(spinlock_t *lock)
{
    t = atomic_inc(lock->next_ticket);
    while (t != lock->current_ticket)
        ; /* Spin */
}
```

```c
void spin_unlock(spinlock_t *lock)
{
    lock->current_ticket++;
}
```

```c
struct spinlock_t {
    int current_ticket;
    int next_ticket;
}
```

前一个锁持有者在发出 N/2 个回复后通知下一个锁持有者

![](img/53ee1e3b0eba43505c7d530851f32f6f_791_0.png)

所有等待者读取锁

## xv6 锁可扩展吗？

```c
// Acquire the lock.
// Loops (spins) until the lock is acquired.
// Holding a lock for a long time may cause
// other CPUs to waste time spinning to acquire it.
void
acquire(struct spinlock *lk)
{
  pushcli(); // disable interrupts to avoid deadlock.
  if(holding(lk))
    panic("acquire");

  // The xchg is atomic.
  // It also serializes, so that reads after acquire are not
  // reordered before it.
  while(xchg(&lk->locked, 1) != 0)
    ;

  // Record info about lock acquisition for debugging.
  lk->cpu = cpu;
  getcallerpcs(&lk, lk->pcs);
}

// Release the lock.
void
release(struct spinlock *lk)
{
  if(!holding(lk))
    panic("release");

  lk->pcs[0] = 0;
  lk->cpu = 0;

  // The xchg serializes, so that reads before release are
  // not reordered after it. The 1996 PentiumPro manual (Volume 3,
  // 7.2) says reads can be carried out speculatively and in
  // any order, which implies we need to serialize here.
  // But the 2007 Intel 64 Architecture Memory Ordering White
  // Paper says that Intel 64 and IA-32 will not move a load
  // after a store. So lock->locked = 0 would work here.
  // The xchg being asm volatile ensures gcc emits it after
  // the above assignments (and after the critical section).
  xchg(&lk->locked, 0);

  popcli();
}
```

## 可扩展锁

## 使票据自旋锁可扩展

常见方法：使用比例退避

```c
void spin_lock(spinlock_t *l) {
    int t = atomic_xadd(&l->next_ticket);
    while (t != lock->current_ticket)
        // wait more time with each failure
        ;
}
```

为什么这会有效？

## 示例修复

```
arch/x86/kernel/smp.c | 23 ++++++++++++++++++-----
1 file changed, 20 insertions(+), 3 deletions(-)
diff --git a/arch/x86/kernel/smp.c b/arch/x86/kernel/smp.c
index 20da354..aa743e9 100644
--- a/arch/x86/kernel/smp.c
+++ b/arch/x86/kernel/smp.c
@@ -117,11 +117,28 @@ static bool smp_no_nmi_ipi = false;
 */
void ticket_spin_lock_wait(arch_spinlock_t *lock, struct __raw_tickets inc)
{
+    __ticket_t head = inc.head, ticket = inc.tail;
+    __ticket_t waiters_ahead;
+    unsigned loops;
+
     for (;;) {
-        cpu_relax();
-        inc.head = ACCESS_ONCE(lock->tickets.head);
+        waiters_ahead = ticket - head - 1;
+        /*
+         * We are next after the current lock holder. Check often
+         * to avoid wasting time when the lock is released.
+         */
+        if (!waiters_ahead) {
+            do {
+                cpu_relax();
+            } while (ACCESS_ONCE(lock->tickets.head) != ticket);
+            break;
+        }
+        loops = 50 * waiters_ahead;
+        while (loops--) {
+            cpu_relax();
+        }
-        if (inc.head == inc.tail)
+        head = ACCESS_ONCE(lock->tickets.head);
+        if (head == ticket)
+            break;
     }
}
```
