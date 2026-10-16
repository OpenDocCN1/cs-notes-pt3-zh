# 4.2.1.2 ORACLE进程

－日志写（Log Writer，LGWR）：

检查点导致LGWR和DBWR。检查点间隔时间越短，发生数据库故障时需要的恢复时间越短，同时减少了必须执行每一检查点所需的工作。当决定正确的检查点间隔时，必须权衡所有这些因素。

LOG_CHECKPOINT_INTERVAL参数即一定数量的操作系统块（不是Oracle块）写入重做时，引起数据库中的一个检查点被触发。LOG_CHECKPOINT_TIMEOUT参数指定的时间间隔（以秒为单位）发生一个检查点。