

## 映射基数约束

- 表示通过一个关系集，一个实体可与多少个另一实体相关联。
- 在描述二元关系集时最为有用。
- 对于二元关系集，映射基数必须是以下类型之一：
  - 一对一
  - 一对多
  - 多对一
  - 多对多

## 映射基数

![](img/5285b20d8f5a79969a3f150d38beebfc_148_0.png)

(a) 一对一

![](img/5285b20d8f5a79969a3f150d38beebfc_148_1.png)

(b) 一对多

注意：A 和 B 中的某些元素可能未映射到另一集合中的任何元素

![](img/5285b20d8f5a79969a3f150d38beebfc_149_0.png)

(a) 多对一

![](img/5285b20d8f5a79969a3f150d38beebfc_149_1.png)

(b) 多对多

注意：A 和 B 中的某些元素可能未映射到另一集合中的任何元素

## 键

- 实体集的**超键**是一个或多个属性的集合，其值能够唯一确定每个实体。
- 实体集的**候选键**是一个最小超键
  - *ID* 是 *instructor* 的候选键
  - *course_id* 是 *course* 的候选键
- 虽然可能存在多个候选键，但其中一个候选键被选为**主键**。

## 关系集的键

- 参与关系集的各个实体集的主键组合构成了该关系集的超键。
  - `(s_id, i_id)` 是 `advisor` 的超键
  - **注意：** 这意味着 *一对实体集在某个特定关系集中最多只能有一个关系。*
    - 例如：如果我们希望记录一个学生与其导师之间的多个会面日期，则不能为每次会面假设一个关系。不过我们可以使用多值属性。
- 在决定哪些是候选键时，必须考虑关系集的映射基数。
- 当存在多个候选键时，选择主键需要考虑关系集的语义。

## 冗余属性

- 假设我们有以下实体集
  - *instructor*，其属性包括 *dept_name*
  - *department*
  以及一个关系
  - *inst_dept*，它关联 *instructor* 和 *department*
- 实体 *instructor* 中的属性 *dept_name* 是冗余的，因为存在一个显式关系 *inst_dept*，它将教师与院系关联起来。
  - 该属性复制了关系中已有的信息，应从 *instructor* 中移除。
  - 但是：在转换回表时，某些情况下该属性会被重新引入，我们稍后会看到。

## E-R 图

![](img/5285b20d8f5a79969a3f150d38beebfc_153_0.png)

- Peter Chen 和 IDEF1X
- 矩形表示实体集。
- 菱形表示关系集。
- 属性列在实体矩形内部。
- 下划线表示主键属性。

## 具有复合、多值和派生属性的实体

| instructor |
|---|
| *ID* |
| *name* |
| &nbsp;&nbsp;&nbsp;&nbsp;*first_name* |
| &nbsp;&nbsp;&nbsp;&nbsp;*middle_initial* |
| &nbsp;&nbsp;&nbsp;&nbsp;*last_name* |
| *address* |
| &nbsp;&nbsp;&nbsp;&nbsp;*street* |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*street_number* |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*street_name* |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*apt_number* |
| &nbsp;&nbsp;&nbsp;&nbsp;*city* |
| &nbsp;&nbsp;&nbsp;&nbsp;*state* |
| &nbsp;&nbsp;&nbsp;&nbsp;*zip* |
| {*phone_number*} |
| *date_of_birth* |
| *age( )* |

## 具有属性的关系集

![](img/5285b20d8f5a79969a3f150d38beebfc_155_0.png)

## 角色

- 一个关系中的实体集不必互不相同。
  - 实体集的每次出现都在关系中扮演一个“角色”。
- 标签 “course_id” 和 “prereq_id” 被称为角色。

![](img/5285b20d8f5a79969a3f150d38beebfc_156_0.png)

