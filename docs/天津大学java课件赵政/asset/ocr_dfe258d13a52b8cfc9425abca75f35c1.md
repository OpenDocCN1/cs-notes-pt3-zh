# 例 P122　　　　　　　　　　　　　　Stack 类的改进版本

```
```java
// This class defines an integer stack that can hold 10 values.
class Stack {
  /* Now, both stck and tos are private. This means
     that they cannot be accidentally or maliciously
     altered in a way that would be harmful to the stack.
  */
  private int stck[] = new int[10]; // 堆栈 stck 和堆栈顶下标 tos,
  private int tos;                  // 都被指定为private

  // Initialize top-of-stack
  Stack() { tos = -1; }

  // Push an item onto the stack
  void push(int item) {              // push()或pop()才能访问或改变
    if(tos==9)
      System.out.println("Stack is full.");
    else
      stck[++tos] = item;
  }
}
```
```