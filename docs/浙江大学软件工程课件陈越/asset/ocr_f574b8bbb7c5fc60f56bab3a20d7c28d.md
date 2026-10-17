# 3.8 Goto and Labels

+   - syntax:
+     goto label_name
+     label_name: statements

Example 1:
for(...)
  for(...) {
    if(disaster)
      goto error;
  }
...
error: clean up the mess