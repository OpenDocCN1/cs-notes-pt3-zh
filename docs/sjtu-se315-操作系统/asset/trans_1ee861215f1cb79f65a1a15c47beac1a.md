

## 死锁 Bug 是如何被修复的？

可能会引入非死锁

- 放弃资源获取 19 (61%)
- 改变资源获取顺序 7 (23%)
- 将资源拆分为更小的资源 1 (3%)
- 其他 4 (13%)

我们需要关注“已修复”死锁 Bug 的正确性

## 其他发现

并发 Bug 的影响

~ 70% 导致程序崩溃或挂起

复现 Bug 对诊断至关重要

程序员缺乏诊断工具

大多数是通过代码审查诊断的

复现 Bug 极其困难且直接决定诊断时间

60% 首次补丁包含并发 Bug（旧的或新的）

## 总结

Bug 检测需要关注顺序违规 Bug 和多变量并发 Bug

测试可以针对更现实的交错覆盖目标

修复并发 Bug 并非易事且不容易做对

需要自动化工具的支持

## 异常处理器中的 BUG

## 一个由 trivial 错误导致的问题

> **用户：**
> 
> “当罕见的资源管理器重启发生时，MapReduce 作业会挂起。*我必须 ssh 到我们集群中的 4000 个节点并杀死所有作业。*”

```
catch (RebootException) {
    // TODO
    LOG(“Error event from RM: shutting down...”);
  + eventHandler.handle(exception_response);
}
```

## 为什么开发者会忽略错误处理？

- 开发者认为错误永远不会发生
- 代码演进可能会使错误成为可能
- 判断可能是错误的

```
} catch (IOException e) {
// will never happen
}
```

- 错误处理很困难
- 错误可能由第三方库返回

```
} catch (NoTransitionException e) {
/* Why this can happen? Ask God not me. */
}
```

- 功能开发被优先考虑

## 其他发现

- 故障只需不超过 3 个节点即可显现
  * 几乎全部 (98%)
- 故障可以通过单元测试离线复现
  - 触发事件记录在系统日志中
  * 日志嘈杂：每个故障打印的日志消息数量的中位数为 824。
- 非确定性故障仍可被确定性地复现
  * 至少一部分时序依赖可以由测试人员控制

## 意外的乐趣：错误处理器中的注释

```
/* If this happens, hell will unleash on earth. */
```

```
/* FIXME: this is a buggy logic, check with alex. */
```

```
/* TODO: this whole thing is extremely brittle. */
```

```
/* TODO: are we sure this is OK? */
```

```
/* I really thing we should do a better handling of these
* exceptions. I really do. */
```

```
/* I hate there was no piece of comment for code
* handling race condition.
* God knew what race condition the code dealt with! */
```

## 操作系统 BUG

## Bug 的代价？？

爱国者导弹防御系统
28 名士兵死亡，98 人受伤

Therac-25 医疗设备
数人死亡，其他人受伤

通用电气 XA/21
5000 万人失去水电。

## Bug 对你意味着什么？

![](img/53ee1e3b0eba43505c7d530851f32f6f_883_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_883_1.png)

學而日古人求學精神

## 本次讲座

典型操作系统 Bug 的一个分析示例

描述操作系统 Bug 查找的几条规则

基于不变量

JOS 中的不变量

## 如何查找 Bug？

你的信念集是什么？

- MUST 集
- MAY 集

隐含集是什么？

不一致意味着可能存在 Bug！！

##  trivial 一致性：NULL 指针

*p 意味着 MUST 信念：

p 不为 null

一次检查 (p == NULL) 意味着两个 MUST 信念：

POST: 在真分支上 p 为 null，在假分支上不为 null
PRE: 检查前 p 未知

```
/* 2.4.1: drivers/isdn/svmb1/capidrv.c */
if (!card)
    printk(KERN_ERR, “capidrv-%d: ...”, card->contrnr..)
```

```
/* drivers/net/wan/sdla_chdlc.c:3948 */
if (!card){
    lock_adapter_irq(&card->wandev.lock,&smp_flags);
    card->tty=NULL;
}
```

