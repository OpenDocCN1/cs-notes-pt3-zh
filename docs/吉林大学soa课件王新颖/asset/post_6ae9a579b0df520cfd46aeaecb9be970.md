
## 服务计算带来分布式计算演进

1980's

1990's

2000's

服务计算

互联网和电子商务

客户-服务器计算

主机计算

投资回报率
互操作性/灵活性
面市时间
基础设施的充分利用

## 时代特征

- 打包定制大型机应用
- 自上而下的程序开发
- 集中式计算模型
- 非分布的解决方案
- 基于新兴的PC技术

- 客户-服务器应用
- 面向对象的开发
- 企业为中心的计算
- Internet扩展
- 电子商务应用

- 企业Web应用程序及套件
- Web服务和软件组件技术
- 新一代集成
- 实时应用组装
- 快速部署与管理

## 计算环境的演变

- 从Socket到RPC
- 通用对象请求代理架构CORBA
- 分布式组件对象模型DCOM
- 服务器组件模型EJB
- 面向服务端计算环境

![](img/431d4828d5c6073b7e23d9eca159cdeb_63_0.png)

基于服务总线技术的传输协议和位置透明的调用方式

客户进程
服务器进程
本地过程调用
系统调用
客户函数
客户句柄
服务器函数
服务器句柄
网络调用
本地内核
远程内核
网络通信

## 远程过程调用流程图

(1)
(10)
(2)
(9)
(3)
(8)
(6)
(5)
(7)
(4)

![](img/431d4828d5c6073b7e23d9eca159cdeb_64_0.png)

协同
Collaboration

SOA

集成
Integration

随需应变
On-Demand

## 服务计算带来中间件技术演进

- 趋势
  - 数字化
  - 网络化
  - 智能化

对象 消息传递

构件 J2EE、CORBA

简单服务 MOM、XML-RPC

Web服务 SOAP、WSDL、UDDI

函数 函数调用

客户/服务器

网络化技术

虚拟计算环境

单机、主机

规模 大型、小型

60年代 70 80 90 2000 2010

### London

London is the capital and largest city of England and the United Kingdom, with a population of just over 9 million.

![](img/431d4828d5c6073b7e23d9eca159cdeb_66_0.png)

London stands on the River Thames in southeast England, at the head of a 50-mile (80 km) estuary down to the North Sea, and has been a major settlement for two millennia.

The City of London, its ancient core and financial centre, was founded by the Romans as Londinium and retains boundaries close to its original medieval limits.

As one of the world's major global cities, London exerts a strong influence on world arts, entertainment, fashion, commerce and finance, education, healthcare, media, science and technology, tourism, and transport.

## 服务计算中的服务

- 从外特性上看，一个服务被定义为显式的、独立于服务具体实现技术细节的接口。

- 从内特性上看，服务封装了可复用的业务功能

![](img/431d4828d5c6073b7e23d9eca159cdeb_68_0.png)

## 服务计算的经典模型

![](img/431d4828d5c6073b7e23d9eca159cdeb_69_0.png)

## 定义Services集

- **定义1——Services集：**
  - 由XML元素名空间所确定的元素名构成的集合称为**元素名集合**，记为$S_e$。
  - 由XML属性名空间所确定的属性名构成的集合称为**属性名集合**，记为$S_a$集合。
  - 由XML属性值构成的集合称为**属性值集合**，记为$S_v$。
- **定义2——XML的元素：**
  - 如果$e$是元素，且$e$没有子元素，则称$e$是**0型元素**。
  - 如果$e$是元素，且$e$仅有0型子元素，则称$e$是**1型元素**。
  - 如果$e$是元素，并且$e$至少有一个$n-1$型子元素，则称$e$是**n型元素**。

## Services 集合示例

```xml
<portType name="BookQuote">
  <operation name="getBookPrice">
    <input name="isbn"
    message="GetBookPriceRequest"/>
    <output name="price"
    message="GetBookPriceResponse"/>
  </operation>
</portType>
```

### Services 集合示例cont.

- S1={<input,name,"isbn">, <input,message,"GetBookPriceRequest">}
- S2={<output,name,"isbn">, <output,message,"GetBookPriceResponse">}
- S3={<operation,name,"getBookPrice">}∪{S1}∪{S2}
- S4={<portType,name,"BookQuote">}∪{S3}

## Services集路径

- 路径表示了元素与子元素的层次关系，它蕴含了 services集合中元素集合与子元素集合之间的包含关系。
- 定义：如果 e₀ 是元素名，则 e₀ 是路径；如果 e₀\e₁\...\eₖ₋₁ 是路径，且 eₖ 是元素名，则 e₀\e₁\...\eₖ 是路径；所有路径集合表示为 Sₚ。
- 路径中元素的 services 集与其子元素的 services 集有包含关系，因此有下面关系：
  - Sₛ(eₙ) ⊆ ...... ⊆ Sₛ(e₁) ⊆ Sₛ(e₀)

## Services集路径示例

```
S4={<portType,name,"BookQuote">,
  {<operation,name,"getBookPrice">,
    {<input,name,"isbn">,
      <input,message,"GetBookPriceRequest">
    },
    {<output,name,"isbn">,
      <output,message,"GetBookPriceResponse">}
    }
  }
}
portType\operation\input  S1⊆S3⊆S4
portType\operation\output  S2⊆S3⊆S4
```

## Services集元操作

- Add函数(+): 添加元素
- Remove函数(-): 删除元素
- 滤波函数(λ): 按路径查找<元素,属,值>
- 选择函数(σ): 按路径查找子元素，属或值，返回一个字符串
- car函数(δ): 按路径查找子元素，返回<元素,属,值>
- cdr函数(θ): 查找元素的完整路径
- 连接函数(τ): 合并两个Services集合

## Services语法

- 乔姆斯基文法 G = < V, T, P, S >
  - 0型文法
  - 1型文法(上下文有关文法)
  - 2型文法(上下文无关文法)
  - 3型文法(正则文法)
- XML文档文法 G = < V, T, P, S >
  - XML文档文法元语言
