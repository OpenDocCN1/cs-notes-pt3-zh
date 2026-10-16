# 例6.4（续）

```
```java
void print() {
    super.print();
    System.out.printf("Sid:%s\n", sid);
}

public static void main(String args[]) {
    Student s1 = new Student("zhang san", "123", "S2012");
    s1.print();
}
```
```