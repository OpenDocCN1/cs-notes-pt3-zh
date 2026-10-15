# Weak Entity Sets (Cont.)

![](bbox=[0.0, 0.02, 0.12, 0.15])

+   - Note: the primary key of the strong entity set is not explicitly stored with the weak entity set, since it is implicit in the identifying relationship.
+   - If course_id were explicitly stored, section could be made a strong entity, but then the relationship between section and course would be duplicated by an implicit relationship defined by the attribute course_id common to course and section