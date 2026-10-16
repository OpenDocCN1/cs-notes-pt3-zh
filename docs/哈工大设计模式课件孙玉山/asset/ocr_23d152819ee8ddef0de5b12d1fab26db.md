# 计算机部件销售的例子-代码

在下面用户图形界面源代码中，省略了大量的语句

```
public class ComputerPartsGUI extends JFrame implements ItemListener{
    private void createPartObjAndVisitParts(ActionEvent e){
        ComputerParts part = null;
        PriceVisitor pv = new PriceVisitor();
        PartsInfoVisitor iv = new PartsInfoVisitor();
        CompositeStructure comStruct = new CompositeStructure();

        //循环语句
        if(part != null){
            comStruct.attach(part);

            comStruct.accept(pv);
            comStruct.accept(iv);
        }
    }
}
```