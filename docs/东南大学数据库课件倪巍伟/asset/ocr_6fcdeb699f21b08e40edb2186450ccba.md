此外，视图更新还会存在一些语义上的问题。

例如：由基表COURSE定义一个春季所开课程的视图SPRING如下：

```
CREATE VIEW SPRING
AS SELECT CNO, LHOUR, CREDIT
FROM COURSE
WHERE SEMESTER= ‘春’ ;
```