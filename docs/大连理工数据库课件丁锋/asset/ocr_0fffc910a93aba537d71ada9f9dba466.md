# # 3级封锁协议

| T₁ | T₂ |
|---|---|
| ① Xlock C 读C= 100 C←C*2 写回C=200 ② | |
| ③ ROLLBACK (C恢复为100) Unlock C ④ | Slock C 等待 等待 等待 等待 获得Slock C 读C=100 Commit C Unlock C |
| ⑤ | |

不读“脏”数据