# # 享元模式

# ## 享元模式实例与解析

# ### 实例一：共享网络设备（无外部状态）

DeviceFactory
- devices : ArrayList = new ArrayList()
- totalTerminal : int = 0
+ DeviceFactory ()
+ getNetworkDevice (String type) : NetworkDevice
+ getTotalDevice () : int
+ getTotalTerminal () : int

NetworkDevice
+ getType () : String
+ use () : void

Switch
- type : String
+ Switch (String type)
+ getType () : String
+ use () : void

Hub
- type : String
+ Hub (String type)
+ getType () : String
+ use () : void