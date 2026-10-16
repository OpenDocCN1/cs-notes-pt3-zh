# 例6.4（续）

```
void print() {
    System.out.printf("Name:%s, Id:%s\n", name, id);
}
};

class Student extends Human {
    String sid;

    Student(String name0, String id0, String sp0) {
        super(name0, id0);
        sid = sp0;
    }
```