# # Persistent Programming Languages

+   - Languages extended with constructs to handle persistent data

+   - Programmer can manipulate persistent data directly

+     - no need to fetch it into memory and store it back to disk (unlike embedded SQL)

+   - Persistent objects:

+     - by class - explicit declaration of persistence

+     - by creation - special syntax to create persistent objects

+     - by marking - make objects persistent after creation

+     - by reachability - object is persistent if it is declared explicitly to be so or is reachable from a persistent object