# # Structures and functions

# ## A better way to pass structure variables

```
struct Student { // for reference sake
string name;
int id;
int grade;
};
```

```
int averageStudentGrades( const Student & s1,
const Student & s2 ) {
return (s1.grade + s2.grade) / 2;
}
```

+   - this way the structures are not copied, which can take time for large structures