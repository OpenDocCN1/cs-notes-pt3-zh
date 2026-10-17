

## Machine Level Programming – Control

- **C Control**
  - if-then-else
  - do-while
  - while, for
  - switch

- **Assembler Control**
  - Conditional jump
  - Conditional move
  - Indirect jump (via jump tables)
  - Compiler generates code sequence to implement more complex control

- **Standard Techniques**
  - Loops converted to do-while or jump-to-middle form
  - Large switch statements use jump tables
  - Sparse switch statements may use decision trees (if-elseif-elseif-else)

## Mechanisms in Procedures

### Passing control

- To beginning of procedure code
- Back to return point

### Passing data

- Procedure arguments
- Return value

### Memory management

- Allocate during procedure execution
- Deallocate upon return

### Mechanisms all implemented with machine instructions

### x86-64 implementation of a procedure uses only those mechanisms required

P(...) {
  ...
  y = Q(x);
  print(y)
  ...
}

int Q(int i)
{
  int t = 3*i;
  int v[10];
  ...
  ...
  return v[t];
}

## Mechanisms in Procedures

Machine instructions implement the mechanisms, but the choices are determined by designers. These choices make up the **Application Binary Interface (ABI)**.

- Deallocate upon return
- **Mechanisms all implemented with machine instructions**
- **x86-64 implementation of a procedure uses only those mechanisms required**

## Today

- **Procedures**
  - **Stack Structure**
  - Calling Conventions
    - Passing control
    - Passing data
    - Managing local data
  - Illustration of Recursion

## x86-64 Stack

- Region of memory managed with stack discipline
  - Memory viewed as array of bytes.
  - Different regions have different purposes.
  - (Like ABI, a policy decision)

## x86-64 Stack

- Region of memory managed with stack discipline

Stack "Bottom"

Stack Pointer: `%rsp`

Stack "Top"

