
## Caller-save Registers

```
push %eax
push argument N
...
push argument 1
call callee
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_472_0.png)

## Calling Convention

- Callee-save registers
  - %ebx, %esi, %edi
  - Saved by callee
  - Caller can use these registers freely
  - Callee must save them before using
  - Callee must restore them before return

## Callee-save Registers

```
call callee
push %ebp
mov %esp, %ebp
push %ebx
...
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_474_0.png)

## Procedure/Function Implementation

- ✔ Invoke callee: call (new instructions)
- ✔ Return to caller: ret (new instructions)
- ✔ Passing data: stack, register
- ✔ Registers: calling convention
- ? Local variable: stack

## Local Variable

- Why not store local variables in registers?
  - No enough registers
  - Array and structures (e.g., a[2])
  - Need address (e.g., &a)

## Local Variable

- **Allocation**
  - Below saved regs or old `%ebp`
  - `move/sub %esp` (e.g., `subl $4, %esp`)
- **De-allocation**
  - `move/add %esp` (e.g., `addl $4, %esp`)
- **Usage**
  - Relative to `%esp`/`%ebp`, (e.g., `movl %eax, 8(%esp)`)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_477_0.png)

## Procedure Call

## Procedure/Function Implementation

- Invoke callee: call (new instructions)
- Return to caller: ret (new instructions)
- Passing data: stack, register
- Registers: calling convention
- Local variable: stack

## Local Variable

- Why not store local variables in registers ?
  - No enough registers
  - Array and structures (e.g., a[2])
  - Need address (e.g., &a)

## Local Variable

- Allocation
  - Below saved regs or old %ebp
  - move/sub %esp, (e.g., subl $4, %esp)
- De-allocation
  - move/add %esp, (e.g., addl $4, %esp)
- Usage
  - Relative to %esp/%ebp, (e.g., movl %eax, 8(%esp))

![](img/b3f8b91675c485f1e811aa092ebbf3d4_481_0.png)

## Put it Together

![](img/b3f8b91675c485f1e811aa092ebbf3d4_482_0.png)

## Put it Together

- 1. Save caller-save registers
  (%eax, %edx, %ecx)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_483_0.png)

## Put it Together

- 1. Save caller-save registers
  (%eax, %edx, %ecx)

- 2. Push actual arguments
  from right to left

![](img/b3f8b91675c485f1e811aa092ebbf3d4_484_0.png)

## Put it Together

- 1. Save caller-save registers (%eax, %edx, %ecx)
- 2. Push actual arguments from right to left
- 3. Call instruction
  - Save return address
  - Transfer control to callee

![](img/b3f8b91675c485f1e811aa092ebbf3d4_485_0.png)

## Put it Together

4. Save caller %ebp

![](img/b3f8b91675c485f1e811aa092ebbf3d4_486_0.png)

## Put it Together

- 4. Save caller %ebp
- 5. Set callee %ebp

![](img/b3f8b91675c485f1e811aa092ebbf3d4_487_0.png)

## Put it Together

- 4. Save caller %ebp
- 5. Set callee %ebp
- 6. Save callee-save registers (%ebx, %edi, %esi)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_488_0.png)

## Put it Together

- 4. Save caller %ebp
- 5. Set callee %ebp
- 6. Save callee-save registers (%ebx, %edi, %esi)
- 7. Allocate space for local variable

![](img/b3f8b91675c485f1e811aa092ebbf3d4_489_0.png)

## Put it Together

...

n-4. save return value in %eax

![](img/b3f8b91675c485f1e811aa092ebbf3d4_490_0.png)

## Put it Together

...

- n-4. save return value in %eax

- n-3. de-allocate local variable

![](img/b3f8b91675c485f1e811aa092ebbf3d4_491_0.png)

## Put it Together

...

- n-4. save return value in %eax
- n-3. de-allocate local variable
- n-2. Restore callee-save registers

![](img/b3f8b91675c485f1e811aa092ebbf3d4_492_0.png)

## Put it Together

...

- n-4. save return value in %eax
- n-3. de-allocate local variable
- n-2. Restore callee-save registers
- n-1. Restore caller %ebp

![](img/b3f8b91675c485f1e811aa092ebbf3d4_493_0.png)
