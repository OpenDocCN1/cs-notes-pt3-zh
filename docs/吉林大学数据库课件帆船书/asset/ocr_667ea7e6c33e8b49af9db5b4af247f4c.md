# Example Queries

+   Find the set of all courses taught in the Fall 2009 semester, and in the Spring 2010 semester
+   
+   {t | ∃s ∈ section (t [course_id] = s [course_id] ∧
+       s [semester] = "Fall" ∧ s [year] = 2009
+   ∧ ∃u ∈ section (t [course_id] = u [course_id] ∧
+       u [semester] = "Spring" ∧ u [year] = 2010 )}

+   Find the set of all courses taught in the Fall 2009 semester, but not in the Spring 2010 semester
+   
+   {t | ∃s ∈ section (t [course_id] = s [course_id] ∧
+       s [semester] = "Fall" ∧ s [year] = 2009
+   ∧ ¬∃u ∈ section (t [course_id] = u [course_id] ∧
+       u [semester] = "Spring" ∧ u [year] = 2010 )}