# 在这种情况下，如果出现故障，如何恢复

Restart时，对每个TID，查两个list:

| Commit list | Active list |  |
|---|---|---|
|  | ✓ | delete TID from active list |
| ✓ | ✓ | redo, delete TID from active list |
| ✓ |  | nothing to do |