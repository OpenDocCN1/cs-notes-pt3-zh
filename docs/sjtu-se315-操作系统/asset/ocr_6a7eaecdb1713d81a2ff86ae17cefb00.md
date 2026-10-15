# File System Durability

Topic: tension between fs perf. and crash recovery

Disk performance is often a #1 bottleneck

"how many seeks will that take?"

Durability != Crash consistency

“Here is all of my data. But some of the metadata is wrong.”

Crash recovery is much harder than performance

"what if a crash occurred at this point?"