
## Design Patterns

### Design Pattern Template

- **Pattern name** — describes the essence of the pattern in a short but expressive name
- **Intent** — describes the pattern and what it does
- **Also-known-as** — lists any synonyms for the pattern
- **Motivation** — provides an example of the problem
- **Applicability** — notes specific design situations in which the pattern is applicable
- **Structure** — describes the classes that are required to implement the pattern
- **Participants** — describes the responsibilities of the classes that are required to implement the pattern
- **Collaborations** — describes how the participants collaborate to carry out their responsibilities
- **Consequences** — describes the “design forces” that affect the pattern and the potential trade-offs that must be considered when the pattern is implemented
- **Related patterns** — cross-references related design patterns

## 3.4 Modular Design

*easier to build, easier to change, easier to fix ...*

![](img/fcdc64f47992afbcce2e20fafbbb0375_237_0.png)

### Modularity: Trade-offs

What is the “right” number of modules for a specific software design?

![](img/fcdc64f47992afbcce2e20fafbbb0375_238_0.png)

## 3.5 Information Hiding

- module
- controlled interface
- clients
- “secret” — a specific design decision
  - algorithm
  - data structure
  - details of external interface
  - resource allocation policy

### Why Information Hiding?

- reduces the likelihood of “side effects”
- limits the global impact of local design decisions
- emphasizes communication through controlled interfaces
- discourages the use of global data
- leads to encapsulation—an attribute of high quality design
- results in higher quality software

## 3.6 Stepwise Refinement

![](img/fcdc64f47992afbcce2e20fafbbb0375_241_0.png)

## 3.7 Functional Independence

COHESION - the degree to which a module performs one and only one function.

COUPLING - the degree to which a module is “connected” to other modules in the system.

## 3.8 Refactoring

Fowler [FOW99] defines refactoring in the following manner:

> “Refactoring is the process of changing a software system in such a way that it does not alter the external behavior of the code [design] yet improves its internal structure.”

When software is refactored, the existing design is examined for

- redundancy
- unused design elements
- inefficient or unnecessary algorithms
- poorly constructed or inappropriate data structures or any other design failure that can be corrected to yield a better design.

## 3.9 Design Classes

- User interface classes – define abstractions necessary for HCI.
- Business domain classes – refinements of analysis classes.
- Process classes – lower-level business abstractions that manage business domain classes.
- Persistent classes – data stores (databases) that persist beyond execution of the software.
- System classes – management and control functions that enable the system to operate and communicate within its computing environment and with the outside world.

### Well-formed Design Class

- **Complete and sufficient** – class should be a complete and sufficient encapsulation of reasonable attributes and methods.
- **Primitiveness[原始性]** – each method should be focused on one thing.
- **High cohesion** – class should be focused on one kind of thing.
- **Low coupling** – collaboration should be kept to an acceptable minimum.

## 4 The Design Model

![](img/fcdc64f47992afbcce2e20fafbbb0375_246_0.png)

过程维度表示设计模型的演化，设计工作作为软件过程的一部分被执行。

抽象维度表示过程的详细级别，分析模型的每个元素转化为一个等价的设计，然后迭代精化。

- process dimension
- abstraction dimension
- high
- low
- analysis model
- design model
- architecture elements
- interface elements
- component-level elements
- deployment-level elements

### Design Model Elements

- Data elements
  - Architectural level → databases and files
  - Component level → data structures
- Architectural elements
  - An architectural model is derived from:
    1. Application domain[应用领域信息]
    2. Analysis model[特定分析模型元素]
    3. Available styles and patterns[体系结构风格和模式]
- Interface elements
  - There are three parts to the interface design element:
    1. The user interface (UI)
    2. Interfaces to external systems
    3. Interfaces to components within the application
- Component elements
- Deployment elements
