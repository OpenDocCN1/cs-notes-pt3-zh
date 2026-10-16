# 运算符概览(1)

| 作用域解析 | class_name::member | 全局 | ::name |
| 作用域解析 | namespace_name::member | 全局 | ::qualified-name |
| 成员选择 | object.member | 下标 | pointer[expr] |
| 成员选择 | pointer->member | 模板 | type(expr_list) |
| 值或引用 | expr(expr_list) | 后置++ | lvalue++ |
| const转换 | const_cast<type>(expr) | 后置-- | lvalue-- |
| 类型查询 | typeof(type) | 不恰当的转换 | reinterpret_cast<type>(expr) |
| 强制类型识别 | type(expr) | 不恰当的转换 | <type>(expr) |
| 强制在静态的转换 | static_cast<type>(expr) |  |  |
| 运行时的检查的转换 | dynamic_cast<type>(expr) |  |  |

# 运算符概览(2)

| 对象大小 | sizeof expr | 容量量 | +=lvalue |
| 类型大小 | sizeof(type) | 容量量 | -=lvalue |
| 地址 | &lvalue | 指针 | -expr |
| 间接访问 | *expr | 事(常数) | l expr |
| 建造(分配) | new type | 一元符号 | -expr |
| 建造(初始化标准化) | new type(expr-list) | 一元符号 | +expr |
| 建造(放置) | new (expr)type |  |  |
| 建造及放置(初始化标准化) | new (expr-list)type(expr-list) | 强制类型转换 | (type)expr |
| 销毁(释放) | delete pointer | 删除数组 | delete []pointer |

# 运算符概览(3)

| 成员选择 | object.*pointer-to-member |  |
| 成员选择 | pointer->*pointer-to-member |  |
| 乘(求余) | expr*expr | 除 | expr/expr |
| 取余(求余) | expr%expr | 加(求和) | expr+expr |
| 减(求差) | expr-expr |  |  |
| 左移 | expr << expr | 右移 | expr>>expr |
| 小于 | expr < expr | 小于等于 | expr <= expr |
| 大于 | expr > expr | 大于等于 | expr >= expr |

# 运算符概览(4)

| 等于 | expr == expr | 不等于 | expr!=expr |
| 按位与 | expr&expr |  |  |
| 按位或 | expr^expr |  |  |
| 按位异或 | expr|expr |  |  |
| 逻辑与 | expr&&expr |  |  |
| 逻辑或 | expr||expr |  |  |