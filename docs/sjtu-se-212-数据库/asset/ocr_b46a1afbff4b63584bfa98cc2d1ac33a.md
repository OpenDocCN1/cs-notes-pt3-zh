# Denormalization for Performance

+   - May want to use non-normalized schema for performance
+   - For example, displaying prereqs along with course_id, and title requires join of course with prereq
+   - Use denormalized relation containing attributes of course as well as prereq with all above attributes
+     - faster lookup
+     - extra space and extra execution time for updates
+     - extra coding work for programmer and possibility of error in extra code