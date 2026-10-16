# 102 基本字节数据流

# ➢读对象数据流

```
Customer c=null;
FileInputStream f=new
FileInputStream("D:/java/f.txt");
ObjectInputStream s=new ObjectInputStream(f);
try{
    c=(Customer)s.readObject(c);
    c.close()
}catch(IOException e){
    e.printStackTrace();
}
```