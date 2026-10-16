# # 重构实践：影片出租店

```
public String statement() {……
    switch(each.getMovie().getPriceCode()){
        case Movie.REGULAR:
```

影片出租店管理程序：计算每一位顾客的消费金额并打印报表（**statement**）。操作人员告诉程序：顾客租了那些影片、租期多长，程序便根据租赁时间和影片类型计算费用。影片分为三类：普通片、儿童片和新片。除了计算费用外，还要为常客计算点数；点数会随着“租片种类是否为新片”而有所不同！

```
……
if ((each.getMovie().getPriceCode() == Movie.NEW_RELEASE) &&
    each.getDaysRented() > 1)
    frequentRenterPoints ++;
……}
```