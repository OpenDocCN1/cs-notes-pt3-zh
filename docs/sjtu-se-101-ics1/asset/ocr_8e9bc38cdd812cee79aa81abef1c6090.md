# Static libraries (archives)

![](bbox=[0.05, 0.22, 0.95, 0.68])

static library (archive) of relocatable object files concatenated into one file.

executable object file (only contains code and data for libc functions that are called from p1.c and p2.c)

Further improves modularity and efficiency by packaging commonly used functions (e.g., C standard library, math library)

Linker selectively only the .o files in the archive that are actually needed by the program.