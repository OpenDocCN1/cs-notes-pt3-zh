# 使用适配器模式进行设计的例子

![](bbox=[0.016, 0.156, 0.959, 0.889])

Customer

<<uses>>

# <<interface>>
AddressValidator

isValidAddress(addr: String, zip: String, state: String): boolean

# USAddress

isValidAddress(addr: String, zip: String, state: String): boolean

# CAAddress

isValidCanadianAddress(addr: String, pcode: String, prvnc: String): boolean

# CAAddressAdapter

isValidAddress(addr: String, zip: String, state: String): boolean

Inside this method,
isValidCanadianAddress
will be called directly

# 使用类适配器模式进行的设计