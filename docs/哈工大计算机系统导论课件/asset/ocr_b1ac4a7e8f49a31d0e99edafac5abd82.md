# 状态变化的控制逻辑

设置条件码

```
# Should the condition codes be updated?
bool set_cc = E_icode == IOPQ &&
# State changes only during normal operation
!m_stat in { SADR, SINS, SHLT }
&& !W_stat in { SADR, SINS, SHLT };
```

阶段控制

也控制访存阶段的更新

```
# Start injecting bubbles as soon as exception passes through memory stage
bool M_bubble = m_stat in { SADR, SINS, SHLT }
|| W_stat in { SADR, SINS, SHLT };

# stall pipeline register W when exception encountered
bool W_stall = W_stat in { SADR, SINS, SHLT };
```

![](bbox=[0.48, 0.02, 0.98, 0.95])