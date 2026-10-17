
## Cache Lab Tips!

- Review cache and memory lectures
  - Ask if you don't understand something

- Start early, this can be a challenging lab!

- Don't get discouraged!
  - If you try something that doesn't work, take a well deserved break,
    and then try again

- Finally, **Good luck on Cache Lab!**

## Appendix

- Valgrind
- Clang / LLVM
- Cache Structure

## Appendix: Valgrind

- Tool used for debugging memory use
  - Finds many potential memory leaks and double frees
  - Shows heap usage over time
  - Detects invalid memory reads and writes
  - To learn more... man valgrind

- Finding memory leaks
  - `$ valgrind --leak-resolution=high --leak-check=full --show-reachable=yes --track-fds=yes ./myProgram arg1 arg2`

## Appendix: Clang / LLVM

- Clang is a (gcc equivalent) C compiler
  - Support for code analyses and transformation
  - Compiler will check you variable usage and declarations
  - Compiler will create code recording all memory accesses to a file
  - Useful for Cache Lab Part B (Matrix Transpose)

## Appendix: Cache Structure

E = 2^e lines per set

S = 2^s sets

Address of word:

t bits | s bits | b bits

tag | set index | block offset

data begins at this offset

valid bit

B = 2^b bytes per cache block (the data)

![](img/be2cf0737cec89669e7b18813ea2d3b7_645_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_645_1.png)
