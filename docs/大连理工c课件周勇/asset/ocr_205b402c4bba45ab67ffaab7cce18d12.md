# # 对象的使用

(3) 可以说明指向对象的指针，  
但不能取私有数据成员的指针或成员函数的地址。  

Location location[10];  
Location *pointLoc = &location[0];  
当pointLoc被加1后，它将指向下一个Location对象

(4) 对象可以作为函数的参数，  
既可作值参也可以作引用参数。  

void display(Location &location) { ... };