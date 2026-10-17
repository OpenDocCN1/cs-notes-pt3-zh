# # E-R Design Decisions(cont.)

# ## 3） Use it as an attribute of an entity or a relationship? e.g.

student(sid,name,sex,age,...,supervisor-id, supervisor-name, supervisor-position,..., class, monitor )

+   - 要从对象的语义独立性和减少数据冗余考虑  
+     student(sid,name,sex,age,...);  
+     supervisor(sup-id, name, position, ...);  
+     stu-sup(sid, sup-id, from, to );  
+     class(classno,specialty,monitor,stu-num);  
+     stu-class(sid,classno);