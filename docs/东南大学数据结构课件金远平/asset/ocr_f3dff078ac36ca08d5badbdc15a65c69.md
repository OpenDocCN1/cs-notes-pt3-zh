# For recursive lists, reference count never becomes 0, even if it is no longer accessible.

![](bbox=[0.016, 0.232, 0.825, 0.472])

After calls to r.~GenList() and s.~GenList(), ref(r)=1, ref(s)=2, but the structure is no longer being used. --- there is no simple way to solve it.

Exercises: P240-6