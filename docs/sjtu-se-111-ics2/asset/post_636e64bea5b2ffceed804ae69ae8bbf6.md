
## Sending Signals from the Keyboard

- Typing `ctrl-z`
  - sends a SIGTSTP signal to the shell
  - The shell catches the signal
  - Sends a SIGTSTP signal to every process in the foreground process group
  - The result is to stop (suspend) the foreground job (default)

## Sending Signals with kill Function

```
#include <sys/types.h>
#include <signal.h>
int kill(pid_t pid, int sig);
returns: 0 if OK, -1 on error
```

- If pid is greater than zero,
  - then the kill function sends signal number sig to process pid
- If pid is less than zero
  - then kill sends signal sig to every process in process group abs(pid)

## Receiving a Signal

- Preconditions
  - When the kernel is returning from an exception handler
  - and is ready to pass control to process p

## Receiving a Signal

- Actions
  - kernel checks the set of unblocked pending signals (`pending & ~blocked`)
  - If this set is empty (the usual case)
    - then the kernel passes control to the next instruction (Iₙₑₓₜ) in the logical control flow of p.
  - However, if the set is nonempty
    - then the kernel chooses some signal k in the set (typically the smallest k)
    - and forces p to receive signal k.

## Receiving a Signal

- The receipt of the signal triggers some action by the process.
- Once the process completes the action, then control passes back to the next instruction (Iₙₑₓₜ) in the logical control flow of p.

![](img/9bd5f6161cb6607b56d2fb964d1b8794_558_0.png)

## Receiving a Signal

- Each signal type has a predefined default action, which is one of the following:
  - The process terminates.
  - The process terminates and dumps core.
  - The process stops until restarted by a SIGCONT signal.
  - The process ignores the signal.

## Receiving a Signal

- SIGKILL
  - The default action is to terminate the receiving process
- SIGCHLD
  - The default action is to ignore the signal.

## Receiving a Signal

- A process can modify the default action associated with a signal
  - by using the `signal` function
  - The only exceptions are SIGSTOP and SIGKILL, whose default actions cannot be changed.

## Signal Function

```
#include <signal.h>
typedef void handler_t(int)
handler_t *signal(int signum, handler_t *handler)
returns: ptr to previous handler if OK, SIG_ERR on error (does not set errno)
```

- Three ways to change default actions:
  - If handler is SIG_IGN, then signals of type signum are ignored.
  - If handler is SIG_DFL, then the action for signals of type signum reverts to the default action.
  - Otherwise, change action to handler (called signal handler)

## Signal Function

- Installing the handler
  - Changing the default action by passing the address of a handler to the `signal` function
- Catching the signal
  - The invocation of the handler
- Handling the signal
  - The execution of the handler

```c
#include "csapp.h"

void handler(int sig) /* SIGINT handler */
{
    printf("Caught SIGINT\n");
    exit(0);
}

int main()
{
    /* Install the SIGINT handler */
    if (signal(SIGINT, handler) == SIG_ERR)
        unix_error("signal error");

    pause(); /* wait for the receipt of a signal */

    exit(0);
}
```

## Signal Function

- Handling the signal
  - When a process catches a signal of type k,
  - the handler installed for signal k is invoked
    - with a single integer argument set to k.
  - When the handler executes its **return** statement,
    - control (usually) passes back to the instruction in the control flow
      - where the process was interrupted by the receipt of the signal.
      - in some systems, interrupted system calls return immediately with an error.

## Signal Function

- The same handler function can be used to catch different types of signals
  - By setting different signal numbers as the argument to the signal handler
