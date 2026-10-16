

# LoadRunner——脚本录制与开发

## Virtual User Generator简介

## VuGen录制原理

LoadRunner通过分析协议，录制用户操作的过程，将其还原成对应协议的API组成的脚本，创建原始的Vuser脚本

## ■ Vuser Script录制流程

![](img/88f667f5480db09ef600e4e177b09268_562_0.png)

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

![](img/88f667f5480db09ef600e4e177b09268_563_0.png)

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

![](img/88f667f5480db09ef600e4e177b09268_565_0.png)
![](img/88f667f5480db09ef600e4e177b09268_565_1.png)

## Vuser Script录制流程

### HTML-based script:

每次用户请求生成单独的函数

特点：直观、易于理解和维护

```
web_url("MercuryWebTours",
    "URL=http://localhost/MercuryWebTours/",
    "Resource=0",
    "RecContentType=text/html",
    "Referer=",
    "Snapshot=t1.inf",
    "Mode=HTML",
    LAST);

lr_think_time(90000);
web_submit_form("login.pl",
    "Snapshot=t2.inf",
    ITEMDATA,
    "Name=username", "Value=test", ENDITEM,
    "Name=password", "Value=test", ENDITEM,
    "Name=login.x", "Value=54", ENDITEM,
    "Name=login.y", "Value=9", ENDITEM,
    LAST);
```

## ■ Vuser Script录制流程

### URL-based script:

捕获所有由用户产生的HTTP请求

特点：详细、伸缩性强

```
web_url("MercuryWebTours",
        "URL=http://localhost/MercuryWebTours/",
        "Resource=0",
        "RecContentType=text/html",
        "Referer=",
        "Snapshot=t1.inf",
        "Mode=HTTP",
        LAST);

web_concurrent_start(NULL);

web_url("header.html",
        "URL=http://localhost/MercuryWebTours/header.html",
        "Resource=0",
        "RecContentType=text/html",
        "Referer=http://localhost/MercuryWebTours/",
        "Snapshot=t2.inf",
        "Mode=HTTP",
        LAST);
```

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

![](img/88f667f5480db09ef600e4e177b09268_568_0.png)
![](img/88f667f5480db09ef600e4e177b09268_568_1.png)
![](img/88f667f5480db09ef600e4e177b09268_568_2.png)

URL：输入被测试系统的URL

Record into Action：默认或“New...”新建Action

注：不同的协议类型此窗口不同

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

### 脚本组成：

1. vuser_init:
Vuser启动时执行一次（例：登录服务器）

2. Action:
可反复迭代执行多次；可以创建多个Action

3. vuser_end:
Vuser退出时执行一次（例：记录注销）

### 脚本语法：C语言

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

![](img/88f667f5480db09ef600e4e177b09268_570_0.png)

- 新建Action
- 插入事务、集合点、注释等
- 修改录制选项

## Vuser Script录制流程

- 创建脚本
- 选择协议
- 设置录制选项
- 开始录制
- 插入命令
- 停止录制

![](img/88f667f5480db09ef600e4e177b09268_571_0.png)

```
include "web_api.h"

Action()
{
    web_add_cookie("PREF-ID=12006111bbde2eb6;NW=1
    web_url("www.google.com",
        "URL=http://www.google.com/",

```

VuGen自动生成的脚本

## Vuser Script录制流程

### 实例演示：WebTours在线订票系统

## 事务(Transaction)

事务：一个或多个用户操作步骤的集合

Vuser script中：

lr_start_transaction()和lr_end_transaction()间的代码块

LoadRunner会对事务进行计时，并反映在测试结果中

![](img/88f667f5480db09ef600e4e177b09268_573_0.png)

## 事务(Transaction)

```
#include "lrv_custom_body.h"

vuser_init()
{
    lr_start_transaction("homepage");

    web_url("MercuryWebTours",
        "URL=http://localhost/MercuryWebTours/",
        "Resource=0",
        "RecContentType=text/html",
        "Referer=",
        "Snapshot=t2.inf",
        "Mode=HTML",
        LAST);

    lr_end_transaction("homepage", LR_AUTO);

    return 0;
}
```

## ■调试与回放脚本

### 调试脚本直到编译通过

![](img/88f667f5480db09ef600e4e177b09268_575_0.png)

### 回放脚本

![](img/88f667f5480db09ef600e4e177b09268_575_1.png)

## 调试与回放脚本

- 运行选项设置
  - Runtime Settings（快捷键：F4）
  - General Options中关于脚本运行的设置
- 运行（Run）：F5
- 单步执行（Run Step By Step）：F10
- 停止（Stop）：Ctrl + F5
- 设置/取消断点（Breakpoint）：F9

