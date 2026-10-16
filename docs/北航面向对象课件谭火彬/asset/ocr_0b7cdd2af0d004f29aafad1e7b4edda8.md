# 类图展示实体类的静态关系

![](bbox=[0.019, 0.244, 0.977, 0.803])

| 实体类 | 属性 |
|---|---|
| Book | isbn: string<br>name: string<br>publisher: string<br>price: double |
| BorrowInfo | start_date: date<br>end_date: date |
| Reader | reader_no: string<br>reader_name: string |

继承关系：Catalog → TechBook、LitBook、NewBook；Reader → Student、Faculty。