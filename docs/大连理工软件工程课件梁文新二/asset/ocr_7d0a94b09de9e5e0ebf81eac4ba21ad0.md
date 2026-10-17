# # 12.3.1 面向对象的单元测试

# ## 2. 例如：

Base::Redefined()含有如下语句  
If (value<0) message ("less");  
else if (value==0) message ("equal");  
else message ("more");  
Derived::Redefined()中定义为  
If (value<0) message ("less");  
else if (value==0) message ("It is equal");  
else  
{message ("more");  
if (value==88)message("luck");}

在原有的测试上，对Derived::Redefined()的测试只需做如下改动：  
将value==0的测试结果期望改动；增加value==88的测试。