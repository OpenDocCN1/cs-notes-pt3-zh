# 例子

```
package com.oo.java;
/**
 * 收银员
 */
public class Cashier {
    public Boolean get(Person person, Integer money){
        Boolean result = person.pay(money); //收银员只需要调用Person的pay方法，无需知道Person当前有多少钱
        if( result ){
            System.out.println(person.getName() + " 付款成功，共 " + money + " 块");
        }
        else{
            System.out.println(person.getName() + " 付款失败");
        }
        return result;
    }
}
```