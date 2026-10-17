```
Manage(String n) { // Manage的构造方法， 初始化父类的name
    super(n);
}

public void showInfo(){
    super.showInfo(); //调用父类的方法
    System.out.println("this is subClass call:"+name);
    System.out.println(department);
}
} // 类 manage结束

public class CoverMethod { // 类CoverMethod
    public static void main(String args[]){
        Manage aa=new Manage("李四");
        aa.name="张三";
        aa.department="经理室";
        aa.getInfo();
    }
}
```