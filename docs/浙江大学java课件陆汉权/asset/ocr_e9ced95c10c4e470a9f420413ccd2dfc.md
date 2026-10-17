# （2）各子类：**定义教材类**

```
```java
class Teaching_book extends Book {

    public Teaching_book(int bookPage,float discount) {
        super(bookPage,discount);
    }

    public void show_kind() {
        System.out.println("The book's kind is teaching book");
    }

    public double getPrice(int bookPage,float discount) {
        return bookPage*0.05*discount;
    }
}  // 其类的结果和代码与前面的几个子类相同
```
```