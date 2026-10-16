# Supplement: Reasons for Process swapped out

|  |  |
|---|---|---|
| Swapping | The operating system needs to release sufficient main memory to bring in a process that is ready to execute. |
| Other OS reason | The operating system may suspend a background or utility process or a process that is suspected of causing a problem. |
| Interactive user request | A user may wish to suspend execution of a program for purpose of debugging or in connection with the use of a resource. |
| Timing | A process may be executed periodically (e.g., an accounting or system monitoring process) and may be suspended while waiting for the next time interval. |
| Parent process request | A parent process may wish to suspend execution of a descendant to examine or modify the suspended process, or to coordinate the activity of various descendants. |