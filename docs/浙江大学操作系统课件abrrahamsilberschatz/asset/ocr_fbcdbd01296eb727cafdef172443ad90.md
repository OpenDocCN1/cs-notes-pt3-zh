# # Fig 6.10 Solaris 2 Scheduling

| global priority | scheduling order | class-specific priorities | scheduler classes | run queue |
|---|---|---|---|---|
| highest | first | real time | kernel threads of real-time LWPs | |
| | | system | kernel service threads | |
| | | interactive and time sharing | kernel threads of interactive and time-sharing LWPs | |
| lowest | last | | | |