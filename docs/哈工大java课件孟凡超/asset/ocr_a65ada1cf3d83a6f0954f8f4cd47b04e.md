# 按钮

未分组

```
public void go(){
Border etched=BorderFactory.cre
Border border=BorderFactory.cre
p.setBorder(border);//设置边框
p.add(cb1);
p.add(cb2);
p.add(cb3);
frame.getContentPane().add(ta,BorderLayout.CENTER);
frame.getContentPane().add(p,BorderLayout.SOUTH);
frame.setSize(400,200);
frame.setVisible(true);
ItemListener il=new ItemListener() {//事件监听器(匿名类)
//事件处理器
public void itemStateChanged(ItemEvent e){
JToggleButton tb=(JToggleButton) e.getSource();//取得事件源
if(tb==cb1){//点击JToggleButton1
ta.append("JToggleButton1"+cb1.isSelected());
}else if(tb==cb2){//点击JToggleButton2
ta.append("\n JToggleButton2"+cb2.isSelected());
}else if(tb==cb3){//点击JToggleButton3
ta.append("\n JToggleButton3"+cb3.isSelected());
}
}
};
cb1.addItemListener(il);//注册事件监听器
cb2.addItemListener(il);//注册事件监听器
cb3.addItemListener(il);//注册事件监听器
}
```

![](bbox=[0.48, 0.03, 0.98, 0.42])