# Views Defined Using Other Views

+   - **create view** *physics_fall_2009* **as**
+     **select** *course.course_id, sec_id, building, room_number*
+     **from** *course, section*
+     **where** *course.course_id = section.course_id*
+       **and** *course.dept_name = 'Physics'*
+       **and** *section.semester = 'Fall'*
+       **and** *section.year = '2009';*
+   
+   - **create view** *physics_fall_2009_watson* **as**
+     **select** *course_id, room_number*
+     **from** *physics_fall_2009*
+     **where** *building= 'Watson';*