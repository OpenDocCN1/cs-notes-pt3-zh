# 工作原理

+   - 上述6个函数之间的关系

内核

init_module（模块加载的时候，注册驱动程序）

radimo_open（打开设备）

radimo_ioctl（查询设备参数）

radimo_request（读写设备）

radimo_release（关闭设备）

cleanup_module（卸载模块和驱动程序）