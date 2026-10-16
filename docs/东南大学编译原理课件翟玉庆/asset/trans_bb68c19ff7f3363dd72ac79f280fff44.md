
## 第6章 类型检查

### 第1节 类型系统

### 2. 类型系统

- 类型系统是为程序的各个不同部分分配类型表达式的一组规则。

**注意：**

1. 类型检查器实现类型系统。
2. 类型系统以语法制导的方式规定。
3. 同一语言的不同编译器或处理器可能使用不同的类型系统。

### 3. 类型的静态与动态检查

- 静态检查（由编译器完成）
- 动态检查（运行后检查）
- 强类型语言（如果其编译器能保证所接受的程序在执行时不会出现类型错误）

### 4. 错误恢复

### 第2节 简单类型检查器的规范

### 1. 一个简单的语言

**1) 源语言的文法**

- P → D; E
- D → D; D | id: T
- T → char | integer | array [num] of T | ^T
- E → literal | num | id | E mod E | E[E] | E^

**2) 翻译方案中保存标识符类型的部分**

- P → D; E
- D → D; D
- D → id: T    { addtype(id.entry, T.type) }
- T → char    { T.type = char }
- T → integer    { T.type = integer }
- T → array [num] of T₁    { T.type = array(1..num, T₁.type) }
- T → ^T₁    { T.type = pointer(T₁.type) }

### 2. 表达式的类型检查

- E → literal    { E.type = char }
- E → num    { E.type = integer }
- E → id    { E.type = lookup(id.entry) }
- E → E₁ mod E₂    { E.type = if (E₁.type == integer) && (E₂.type == integer) integer else type_error }
- E → E₁[E₂]    { E.type = if (E₂.type == integer) && (E₁.type == array(s, t)) t else type_error }
- E → E₁^    { E.type = if (E₁.type == pointer(t)) t else type_error }

### 3. 语句的类型检查

- S → id := E    { S.type = if (id.type == E.type) void else type_error }
- S → if E then S₁    { S.type = if (E.type == boolean) S₁.type else type_error }
- S → while E do S₁    { S.type = if (E.type == boolean) S₁.type else type_error }
- S → S₁; S₂    { S.type = if (S₁.type == void) && (S₂.type == void) void else type_error }

### 4. 函数的类型检查

- T → T₁ → T₂    { T.type = T₁.type → T₂.type }
- E → E₁(E₂)    { E.type = if (E₂.type == s) && (E₁.type == s → t) t else type_error }

### 第3节 类型表达式的等价性

### 1. 类型表达式的结构等价性

- 相同的基本类型
- 通过对结构等价的类型应用相同的构造器而形成

### 2. 类型表达式的名称

```
type link = ^cell
```

### 3. 类型表示中的循环

```
type link = ^cell;
cell = record
  info: integer;
  next: link
end;
```

### 第4节 类型转换

- **强制转换**
  - 隐式类型转换
- **显式转换**
  - `Chr(55)`

## 第7章 运行时环境

### 第0节 概述

### 1. 程序与程序执行

- 一个程序由若干过程（函数）组成
- 程序的执行被称为进程
- 程序的执行会导致相关过程的激活
- 过程中的一个名字（例如变量名）会关联到不同的数据对象

**注意：** 一次激活可能会操纵为其分配的数据对象。

