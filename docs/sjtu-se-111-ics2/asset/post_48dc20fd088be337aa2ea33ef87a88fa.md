
## Case 2

Part 3

- Program binary and shared library are touched in the sequence of:
  - Parent process: <page4, page5, stack, page0, page2, bss, heap, fork, page1>
  - Child Process: <stack, page1, page3, bss, page0, page2, heap>
  - Operations for data/bss/stack/heap are write
  - Don't consider reap

## Case 2

- A simple first-hit memory allocation policy is used.

```
slot_t *find_a_mem_slot()
{
    for(i = 0; i < 16; i++)
        if (slot_is_free)
            return slot[i];

    if (i == 16)
        return fail;
}
```

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:

Page4 Stack

Page5 PPN: 3

Stack

Page0 PPN: 1
PPN: 0

Page2

Bss PPN: 8
PPN: 7

Heap PPN: 6

Fork PPN: 4

Parent Process

stack 47 PPN:10 stack 47

page5 page4 16 PPN:1 PPN:0 page5 page4 16

heap bss page3 page2 page1 page0 0

PPN:8 PPN:7 PPN:6 PPN:4

Child Process

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:
Page4 Stack
Page5 Page1 PPN: 3
Stack
Page0 PPN: 1
PPN: 0
Page2
Bss PPN: 8
PPN: 7
Heap PPN: 6
Fork PPN: 4

Parent Process
stack 47 PPN:10
page5
page4 16 PPN:1 PPN:0
heap
bss
page3
page2
page1
page0 0

Child Process
stack 47
page5
page4 16
heap
bss
page3
page2
page1
page0 0

PPN:10
PPN:1
PPN:0
PPN:8
PPN:7
PPN:6
PPN:11
PPN:4

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:

Page4 Stack

Page5 Page1 PPN:3

Stack Page3

Page0 PPN:1 PPN:0

Page2

Bss PPN:8 PPN:7

Heap PPN:6

Fork PPN:4

Parent Process

stack 47 PPN:10 stack 47

page5 page4 16 PPN:1 PPN:0 page5 page4 16

heap bss PPN:8 PPN:7 heap bss

page3 page2 PPN:12 PPN:6 page2

page1 page0 PPN:11 PPN:4 page1 page0

Child Process

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1073_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1073_1.png)

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:

Page4 Stack

Page5 Page1 PPN:3

Stack Page3

Page0 Bss PPN:1 PPN:0

Page2

Bss PPN:8 PPN:7

Heap PPN:6

Fork PPN:4

Parent Process

stack 47 PPN:10 stack 47

page5 page4 16 PPN:1 PPN:0 page5 page4 16

heap bss page3 page2 page1 page0 0

PPN:8 PPN:13 PPN:12 PPN:6 PPN:11 PPN:4

Child Process

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:

Page4 Stack

Page5 Page1 PPN: 3

Stack Page3

Page0 Bss PPN: 1
PPN: 0

Page2 Page0

Bss PPN: 8
PPN: 7

Heap PPN: 6

Fork PPN: 4

Parent Process

stack 47

page5
page4 16

heap
bss
page3
page2
page1
page0 0

PPN:10

PPN:1
PPN:0

PPN:8
PPN:13
PPN:12
PPN:6
PPN:11
PPN:4

Child Process

stack 47

page5
page4 16

heap
bss
page3
page2
page1
page0 0

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:
Page4 Stack
Page5 Page1 PPN:3
Stack Page3
Page0 Bss PPN:1
PPN:0
Page2 Page0
Bss Page2 PPN:8
PPN:7
Heap PPN:6
Fork PPN:4

Parent Process
stack 47 PPN:10
page5 PPN:1
page4 16 PPN:0
heap PPN:8
bss PPN:13
page3 PPN:12
page2 PPN:14
page1 PPN:11
page0 PPN:4 0

Child Process
stack 47
page5 16
page4
heap
bss
page3
page2
page1
page0 0

## Case 2

- Please fill in the flat page tables with PPN below for both the parent process and the child process just before they finished executing.

Parent: Child:

Page4 Stack

Page5 Page1 PPN:3

Stack Page3

Page0 Bss PPN:1 PPN:0

Page2 Page0

Bss Page2 PPN:8 PPN:7

Heap Heap PPN:6

Fork PPN:4

Parent Process

stack 47 PPN:10

page5 page4 16 PPN:1 PPN:0

heap bss page3 page2 page1 page0 0 PPN:15 PPN:13 PPN:12 PPN:14 PPN:11 PPN:4

Child Process

stack 47

page5 page4 16

heap bss page3 page2 page1 page0 0
