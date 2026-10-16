# UML2.0

# Infrastructure

Defines basic constructs to specify UML and to customize it for specific domains (e.g., real-time)

UML元模型遵循以下的设计原则：

+   - 模块性。这一个原则具有高内聚性和低耦合性，可以运用它们把整个结构分为若干包，按照特征组织每一个元类。

+   - 层次性。层次性以两种方法运用于UML元模型。第一，包的层次结构使元语言核心结构独立于使用它们的高层结构。第二，四层结构的元模型体系结构模式用于隔离各抽象层的关系（尤其是实例化）。

+   - 可分区性。可分区性用于组织相同层的概念域。对于基础结构库，粒度小的分区用来提供当前和将来元建模标准所需的灵活性。对于UML元模型，为了增强包的内聚力，减弱包的耦合性，分区的粒度较大。

# UML2.0

# Infrastructure

Defines basic constructs to specify UML and to customize it for specific domains (e.g., real-time)

+   - 可扩展性。UML可以以两种方式扩展：
+     1）通过使用外廓（profile）为专用平台（比如，J2EE/EJB、NET/COM+）和领域（比如，金融，电信，航空）定制UML语言。
+     2）可以通过重用基础结构库中包的部分内容，增加适当的元类和元关系，来描述和UML相关的新语言。
+     前者定义了专用的UML，后者定义了UML语言系列中的新成员。

+   - 重用性。一个细粒度、灵活的元模型库可以用来自定义UML元模型，同时也可以用来定义其他相关的元模型，比如，Meta Object Facility（元对象机制，MOF）和Common Warehouse Model（公共仓库模型，CWM）。