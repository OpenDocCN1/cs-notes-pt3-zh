# Object 类定义的方法及其用途

| 方法 | 用途 |
|---|---|
| `Object clone()` | 创建一个和被复制的对象完全一样的新对象 |
| `boolean equals(Object object)` | 判断对象内容是否相等 |
| `void finalize()` | 在一个不常用的对象被使用前调用 |
| `Class getClass()` | 获取运行时一个对象的类 |
| `int hashCode()` | 返回调用对象有关的散列值 |
| `void notify()` | 恢复一个等待调用对象线程的执行 |
| `void notifyAll()` | 恢复所有等待调用对象线程的执行 |
| `String toString()` | 返回描述对象的一个字符串，`println()` 输出时自动调用。很多类重载该方法。 |
| `void wait()` | 等待另一个线程的执行 |
| `void wait(long milliseconds)` | 等待指定毫秒数 |
| `void wait(long milliseconds, int nanoseconds)` | 等待指定毫秒数和纳秒数 |

注：`getClass()`、`notify()`、`notifyAll()` 和 `wait()` 被定义成 `final`。