# 2.3 Java的基本数据类型

# 3 变量、说明和赋值

```
public class Assign {

    /**
     * @param args
     */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        byte b;                         //说明byte型变量
        short s=32767;                  //说明short型变量并赋值
        int i=2147483647;               //说明int型变量并赋值
        int i1=0x77, i2=0xBABE;         //说明int型变量并赋值
        long l=9223372036854775807L;    //说明long型变量并赋值
        char c='a';                     //说明字符型变量并赋值
        float f=3.4028235e+38f;         //说明单精度浮点型变量并赋值
        double d=1.7976931348623157e+308d; //说明双精度浮点型变量并赋值
        boolean b1=true;

        long f1= i;                     //自动转换
        byte b1=(byte)i1; //强制转换
        System.out.println("f1="+f1);
        System.out.println("b1="+b1);
    }
}
```