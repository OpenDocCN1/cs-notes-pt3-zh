# # (4) Keys（码、键）

+   Let K ⊆ R

+   K is a superkey（超码）of R if values for K are sufficient to identify a unique tuple of each possible relation r(R)

+   Example: { student-id, student-name } and { student-id } are both superkeys of student.

+   K is a candidate key（候选码）if K is minimal superkey. Example: {student-id} is a candidate key for student, since it is a superkey, and no subset of it is a superkey.

+   K is a primary key（主码）, if k is a candidate key and been defined by user explicitly. Primary key is usually marked by underline.