
## Chapter 7 Runtime Environments
### Section 0 Overview

+ 2. Allocation and de-allocation of data objects
  - Managed by the run-time support package
  - Allocation of a data object is just to allocate storage space to the data object relating to the name in the procedure

Notes: The representation of a data object at run time is determined by its type.

### 3. Activation Trees

A tree to depict the control flow enters and leaves activation of a procedure

![](img/353f619caa6c5715591f2105bdfa2865_425_0.png)

Enter f(4)
Enter f(3)
Enter f(2)
Enter f(1)
Leave f(1)
Enter f(0)
Leave f(0)
Leave f(2)
Enter f(1)
Leave f(1)
Leave f(3)

Enter f(2)
Enter f(1)
Leave f(1)
Enter f(0)
Leave f(0)
Leave f(2)
Leave f(4)

### 4. Control stacks

A stack to keep track of live procedure activations

### 5. Bindings of Names

When an environment associates storage location s with a name x, we say that x is bound to s; the association itself is referred to as a binding of x.

Notes: 1) Even each name is declared once in a program, the same name may denote different object at run time
2) The “ data object” corresponds to a storage location that can hold values

Notes: 3) In programming language semantics, the term “environment” refers to a function that maps a name to a storage location, and term “state” refers to a function that maps a storage location to the value held there.

![](img/353f619caa6c5715591f2105bdfa2865_428_0.png)

+ 4) Environments and states are different; an assignment changes the state, but not the environment

+ 5) If x is not of a basic type, the storage s for x may be a collection of memory words

+ 6) A binding is the dynamic counterpart of a declaration

## Chapter 7 Runtime Environments
### Section 1 Storage organization
#### 2. Activation Records/Frames

+ 1) Definition

A contiguous block of storage that stores information needed by a single execution of a procedure

#### 2) A general activation record

| Returned value |
| Actual parameters |
| Optional control link |
| Optional access link |
| Saved machine status |
| Local data |
| temporaries |

In a stack frame (activation record) we hold the following information:

+ 1) dynamic link: pointer value of the previous stack frame so we can reset the top of stack when we exit this routine.
+ 2) static link: in languages (like Pascal but not C) that allow nested routine declarations, then a routine may be able to access the variables of the routine(s) within which it is declared. In the static link, we hold the pointer value of the stack frame in which the current pointer was declared.
+ 3) return address: point in the code to which we return at the end of execution of the current routine.
+ 4) values of arguments passed to the routine and locals declared in the routine.

Here is what happens when we call a routine:

+ 1) set up new stack frame at top of the stack
+ 2) copy arguments across to new stack frame
+ 3) save existing stack pointer in dynamic link of new frame
+ 4) set up static link if appropriate
+ 5) save return address in new frame
+ 6) set stack pointer to base of new stack frame (this allows access to all variables in the stack frame)
+ 7) jump to the code for the routine

On return we do the reverse:

+ 1) retrieve return address from the stack frame
+ 2) restore stack pointer from dynamic link
+ 3) save result of routine in restored stack frame
+ 4) jump to the return address
