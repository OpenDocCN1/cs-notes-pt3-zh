# 4. Case Study

+   - **Processing Algorithm**
+   - The main function controls the execution of the KWIC program:
+   - The input function is called to read and parse the lines from an input file. This function reads and processes all lines at once and represents it by means of the character (chars_) and line index (line_index_) array, as described before.
+   - The main function calls the circularShift function, which produces circular shifts of each particular line and stores it in the circular shifts array (circular_shifts_), as discussed before.
+   - After the circular shifts have been produced, the main function calls the sort function, which sorts circular shifts alphabetically. The result is stored in the alphabetized array (alphabetized_), as described before.
+   - Finally, the main function calls the output function, prints the sorted lines.

![](bbox=[0.77, 0.77, 0.98, 0.95])