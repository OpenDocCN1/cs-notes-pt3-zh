
## 范式分解

- R = (A, B, C)

F = {A→B, B→C, B→A}

- R1 = (A, B), R2 = (A, C)

Lossless-join decomposition:

R1 ∩ R2 = {A} and A→AB

dependency preserving?

B→C?

(F1 ∪ F2 ∪ ... ∪ Fn)+ = F+

## 范式分解

R(T,S,C)，每位教师T只上一门课C，每门课可能有多个教学班，S为学生。

T→C, SC→T

Key: SC, TS

分解: R1(T,C), R2(T,S)

无损连接，依赖保持？

## 例子

- 图书馆
  - ISBN，分类号：TP311.13

## MVD

- inst_info(ID, child_name, phone_number)

| ID | Child_name | Phone_number |
|---|---|---|
| 99999 | David | 512-555-1234 |
| 99999 | David | 512-555-4321 |
| 99999 | William | 512-555-1234 |
| 99999 | William | 512-555-4321 |

- BCNF, why?
- 仍有冗余，仍有异常
- MVD
  - ID →→ child_name
  - ID →→ phone_number

## MVD

|  | α | β | R − α − β |
|---|---|---|---|
| t₁ | a₁ ... aᵢ | aᵢ₊₁ ... aⱼ | aⱼ₊₁ ... aₙ |
| t₂ | a₁ ... aᵢ | bᵢ₊₁ ... bⱼ | bⱼ₊₁ ... bₙ |
| t₃ | a₁ ... aᵢ | aᵢ₊₁ ... aⱼ | bⱼ₊₁ ... bₙ |
| t₄ | a₁ ... aᵢ | bᵢ₊₁ ... bⱼ | aⱼ₊₁ ... aₙ |

## MVD

- 平凡的MVD, α →→ β, α ∪ β = R
- If α → β then α →→ β
- If α →→ β then α →→ R - α - β

## 4NF

- 对所有的非平凡多值依赖，其决定因子均来自超码。

| ID | Child_name | Phone_number |
|---|---|---|
| 99999 | David | 512-555-1234 |
| 99999 | David | 512-555-4321 |
| 99999 | William | 512-555-1234 |
| 99999 | William | 512-555-4321 |

- ID→→child_name
- ID→→phone_number
- R1(ID,child_name), R2(ID,phone_number)

## ER Model and Normalization

In a real (imperfect) design, there can be functional dependencies from non-key attributes of an entity to other attributes of the entity.

- Example: an *employee* entity with attributes *department_name* and *building*, and a functional dependency
  `department_name → building`
- Good design would have made department an entity

## Denormalization for Performance

- May want to use non-normalized schema for performance
- For example, displaying prereqs along with course_id, and title requires join of course with prereq
- Use denormalized relation containing attributes of course as well as prereq with all above attributes
  - faster lookup
  - extra space and extra execution time for updates
  - extra coding work for programmer and possibility of error in extra code

## Transaction (事务)

## Transaction Concept

- A **transaction** is a unit of program execution that accesses and possibly updates various data items
- SQL DML/C++ Java
- 操作的集合、逻辑工作单元
- 可能由多条语句构成

## Example of transaction

E.g. transaction to transfer $50 from account A to account B:

1. read(A)
2. A := A - 50
3. write(A)
4. read(B)
5. B := B + 50
6. write(B)

## ACID Properties

- Atomicity
- Consistency
- Isolation
- Durability

## Transaction

- Commit

![](img/5285b20d8f5a79969a3f150d38beebfc_270_0.png)

- Rollback

![](img/5285b20d8f5a79969a3f150d38beebfc_270_1.png)

## Transaction process

![](img/5285b20d8f5a79969a3f150d38beebfc_271_0.png)

## Transaction State

![](img/5285b20d8f5a79969a3f150d38beebfc_272_0.png)

## Schedules

- 指令执行的时间顺序
- 必须包含被调度的事务的所有指令，并保持指令在各事务中的原顺序
- 调度，实现事务的并发运行
- 可串行调度，多事务并发运行的结果，与串行运行一致

## Schedule 1

| T₁ | T₂ |
|---|---|
| read(A)<br>A := A - 50<br>write(A)<br>read(B)<br>B := B + 50<br>write(B)<br>commit | |
| | read(A)<br>temp := A * 0.1<br>A := A - temp<br>write(A)<br>read(B)<br>B := B + temp<br>write(B)<br>commit |

A serial schedule in which T₁ is followed by T₂

## Schedule 2

| T₁ | T₂ |
|---|---|
| | read(A)<br>temp := A * 0.1<br>A := A - temp<br>write(A)<br>read(B)<br>B := B + temp<br>write(B)<br>commit |
| read(A)<br>A := A - 50<br>write(A)<br>read(B)<br>B := B + 50<br>write(B)<br>commit | |

A serial schedule where T₂ is followed by T₁

## Schedule 3

| $T_1$ | $T_2$ |
|---|---|
| read(A)<br>$A := A - 50$<br>write(A)<br>read(B)<br>$B := B + 50$<br>write(B)<br>commit | read(A)<br>$temp := A * 0.1$<br>$A := A - temp$<br>write(A)<br>read(B)<br>$B := B + temp$<br>write(B)<br>commit |

In Schedules 1, 2 and 3, the sum A + B is preserved.
