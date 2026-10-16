# 多重处理的例子

运行“top”

+   - 有185个进程，
+   - 以进程ID (PID)

```
top - 20:58:14 up 5:23, 1 user, load average: 1.34, 0.45, 0.20
Tasks: 185 total, 2 ru
%Cpu(s): 42.3 us, 23.7
KiB Mem : 2036780 total
KiB Swap: 2094076 total
PID USER PR NI
14136 linda 20 0
8663 linda 20 0
14018 linda 20 0
7845 root 20 0
8730 linda 20 0
33 root 20 0
6 root 20 0
194 root 0 -20
7665 root 20 0
7796 root 20 0
7894 nobody 20 0
9048 linda 20 0
13894 linda 20 0
1 root 20 0
2 root 20 0
```

# 任务管理器

| 名称 | PID | 状态 | 用户名 | CPU | 内存/专用工 | 描述 |
|---|---|---|---|---|---|---|
| SynTPLpr.exe | 8292 | 正在运行 | simple | 00 | 1,248 K | TouchPad Driver Helper Application |
| SystemSett... | 14512 | 已暂停 | simple | 00 | 128 K | 设备 |
| taskhostw... | 7132 | 正在运行 | simple | 00 | 4,008 K | Windows 任务的主机进程 |
| Taskmgr.exe | 9540 | 正在运行 | simple | 01 | 10,268 K | 任务管理器 |
| TpShocks.exe | 6764 | 正在运行 | simple | 00 | 212 K | Active Protection System |
| TsService.exe | 10468 | 正在运行 | SYSTE... | 00 | 9,468 K | TsService |
| TXPlatform... | 4808 | 正在运行 | simple | 00 | 556 K | 腾讯QQ多客户端管理服务 |
| unsecapp.exe | 3940 | 正在运行 | SYSTE... | 00 | 792 K | Sink to receive asynchronous callback |
| unsecapp.exe | 9664 | 正在运行 | simple | 00 | 820 K | Sink to receive asynchronous callback |
| Video.UI.exe | 5976 | 已暂停 | simple | 00 | 124 K | Video Application |
| wininit.exe | 656 | 正在运行 | SYSTE... | 00 | 620 K | Windows 启动应用程序 |
| winlogon.exe | 2888 | 正在运行 | SYSTE... | 00 | 1,108 K | Windows 登录应用程序 |
| wlanext.exe | 2280 | 正在运行 | SYSTE... | 00 | 1,940 K | Windows Wireless LAN 802.11 Extens |
| WmiPrvSE.exe | 3996 | 正在运行 | SYSTE... | 00 | 1,868 K | WMI Provider Host |
| WmiPrvSE.exe | 9784 | 正在运行 | NETW... | 02 | 4,300 K | WMI Provider Host |
| WRU.exe | 3924 | 正在运行 | simple | 00 | 11,248 K | Intel(R) WiDi Receiver Updater |
| WUDFHost.exe | 1144 | 正在运行 | LOCA... | 00 | 1,480 K | Windows 驱动程序基础 - 用户模式驱动 |
| WUDFHost.exe | 2228 | 正在运行 | LOCA... | 00 | 572 K | Windows 驱动程序基础 - 用户模式驱动 |
| ZeroConfig... | 3144 | 正在运行 | PROSE... | 00 | 2,484 K | Intel(R) PROSet/Wireless Zero Config |
| 系统中断 | - | 正在运行 | SYSTE... | 02 | K | 延迟过编程器和中断例程 |
| 系统和压缩... | 4 | 正在运行 | SYSTE... | 00 | 49,516 K | NT Kernel & System |
| 系统空闲进程 | 0 | 正在运行 | SYSTE... | 92 | 4 K | 处理器空闲时间百分比