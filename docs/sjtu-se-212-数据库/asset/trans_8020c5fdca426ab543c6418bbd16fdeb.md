

## ER 与 UML 类图对比

## ER 图符号

## UML 中的等价表示

n 元关系

重叠泛化

重叠

不相交泛化

不相交

*泛化可以使用合并或分离的箭头，且与重叠/不相交无关*

![](img/5285b20d8f5a79969a3f150d38beebfc_208_0.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_208_1.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_208_2.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_208_3.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_208_4.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_208_5.png)

![](img/5285b20d8f5a79969a3f150d38beebfc_210_0.png)

## 第7章结束

数据库系统概念，第6版

©Silberschatz, Korth and Sudarshan

参见 www.db-book.com 了解重用条件

## 图 7.01

| ID | 姓名 |
|---|---|
| 76766 | Crick |
| 45565 | Katz |
| 10101 | Srinivasan |
| 98345 | Kim |
| 76543 | Singh |
| 22222 | Einstein |

*教师*

| ID | 姓名 |
|---|---|
| 98988 | Tanaka |
| 12345 | Shankar |
| 00128 | Zhang |
| 76543 | Brown |
| 76653 | Aoi |
| 23121 | Chavez |
| 44553 | Peltier |

*学生*

## 图 7.02

教师

学生

![](img/5285b20d8f5a79969a3f150d38beebfc_212_0.png)

## 图 7.03

![](img/5285b20d8f5a79969a3f150d38beebfc_213_0.png)

## 图 7.05

![](img/5285b20d8f5a79969a3f150d38beebfc_215_0.png)

(a)

(b)

## 图 7.06

![](img/5285b20d8f5a79969a3f150d38beebfc_216_0.png)

(a)

(b)

## 图 7.07

![](img/5285b20d8f5a79969a3f150d38beebfc_217_0.png)

## 图 7.08

![](img/5285b20d8f5a79969a3f150d38beebfc_218_0.png)

## 图 7.09

![](img/5285b20d8f5a79969a3f150d38beebfc_219_0.png)

(a)

![](img/5285b20d8f5a79969a3f150d38beebfc_219_1.png)

(b)

![](img/5285b20d8f5a79969a3f150d38beebfc_219_2.png)

(c)

## 图 7.10

![](img/5285b20d8f5a79969a3f150d38beebfc_220_0.png)

| 教师 | 学生 |
|---|---|
| **ID**  
姓名  
工资 | **ID**  
姓名  
总学分 |

## 图 7.11

| 教师 |
|---|
| ID |
| 姓名 |
| ├─ 名字 |
| ├─ 中间名首字母 |
| ├─ 姓 |
| 地址 |
| ├─ 街道 |
| │  ├─ 街道号 |
| │  ├─ 街道名 |
| │  └─ 公寓号 |
| ├─ 城市 |
| ├─ 州 |
| └─ 邮编 |
| { 电话号码 } |
| 出生日期 |
| 年龄( ) |

## 图 7.12

![](img/5285b20d8f5a79969a3f150d38beebfc_222_0.png)

## 图 7.13

![](img/5285b20d8f5a79969a3f150d38beebfc_223_0.png)

## 图 7.14

![](img/5285b20d8f5a79969a3f150d38beebfc_224_0.png)

## 图 7.15

## 图 7.17

![](img/5285b20d8f5a79969a3f150d38beebfc_226_0.png)

## 图 7.18

![](img/5285b20d8f5a79969a3f150d38beebfc_227_0.png)

## 图 7.19

(a)

(b)

## 图 7.20

|  | 教师 |
|---|---|
| 76766 | Crick |
| 45565 | Katz |
| 10101 | Srinivasan |
| 98345 | Kim |
| 76543 | Singh |
| 22222 | Einstein |

教师

|  |  |  |
|---|---|---|
| 98988 | Tanaka | 2009年5月 |
| 12345 | Shankar | 2007年6月 |
| 00128 | Zhang | 2006年6月 |
| 76543 | Brown | 2009年6月 |
| 76653 | Aoi | 2007年6月 |
| 23121 | Chavez | 2007年5月 |
| 44553 | Peltier | 2006年5月 |

学生

## 图 7.21

![](img/5285b20d8f5a79969a3f150d38beebfc_230_0.png)

## 图 7.22

![](img/5285b20d8f5a79969a3f150d38beebfc_231_0.png)

## 图 7.23

![](img/5285b20d8f5a79969a3f150d38beebfc_232_0.png)

## 图 7.24

实体集

关系集

弱实体集的标识性关系集

实体集在关系中的全参与

多对多关系

一对一关系

角色名称
角色指示符

全（不相交）泛化

属性：简单（A1）、复合（A2）、多值（A3）和派生（A4）

主键

弱实体集的区分属性

多对一关系

基数限制

ISA：泛化或特化

不相交泛化

## 图 7.25

具有简单属性 A1、复合属性 A2、多值属性 A3、派生属性 A4 和主键 A1 的实体集 E

![](img/5285b20d8f5a79969a3f150d38beebfc_234_0.png)

多对多关系

![](img/5285b20d8f5a79969a3f150d38beebfc_234_1.png)

一对一关系

![](img/5285b20d8f5a79969a3f150d38beebfc_234_2.png)

多对一关系

![](img/5285b20d8f5a79969a3f150d38beebfc_234_3.png)

在 R 中的参与：全参与（E1）和部分参与（E2）

![](img/5285b20d8f5a79969a3f150d38beebfc_234_4.png)

弱实体集

![](img/5285b20d8f5a79969a3f150d38beebfc_234_5.png)

泛化

![](img/5285b20d8f5a79969a3f150d38beebfc_234_6.png)

全泛化

![](img/5285b20d8f5a79969a3f150d38beebfc_234_7.png)

