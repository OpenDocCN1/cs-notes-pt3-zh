# Thread Exit

```
1 procedure EXIT_THREAD()
2   ACQUIRE (thread_table_lock)
3   thread_table[tid].kill_or_continue ← KILL
4   ENTER_PROCESSOR_LAYER (GET_THREAD_ID (), CPUID)
```

```
procedure ENTER_PROCESSOR_LAYER (tid, processor)
  thread_table[tid].state ← RUNNABLE
  thread_table[tid].topstack ← SP        //
  SP ← processor_table[processor].topstack  //
  return
```

```
procedure EXIT_PROCESSOR_LAYER (processor, tid) //
  processor_table[processor].topstack ← SP  //
  SP ← thread_table[tid].topstack          //
  return
```

```
procedure SCHEDULER ()
  while shutdown = FALSE do
    ACQUIRE (thread_table_lock)
    for i from 0 until 7 do
      if thread_table[i].state = RUNNABLE then
        thread_table[i].state ← RUNNING
        processor_table[CPUID].thread_id ← i
        EXIT_PROCESSOR_LAYER (CPUID, i)
        if thread_table[i].kill_or_continue = KILL then
          thread_table[i].state ← FREE
          DEALLOCA TE(thread_table[i].stack)
          thread_table[i].kill_or_continue = CONTINUE
    RELEASE (thread_table_lock)
    return                      // Go shut dow
```

# Thread
Exit

![](bbox=[0.19, 0.68, 0.82, 0.82])