# 数据依赖

+   • 函数依赖

| Sno | Dname | DLeader |
|------|-------|----------|

+   • Sno → DName, DName → DLeader

+   • 形式化定义

在关系模式R(U)中，如果X→Y，Y→Z，且 Y ⊈ X，Y↛X，则称Z传递函数依赖于X。
注: 如果Y→X, 即X←→Y, 则Z直接依赖于X。