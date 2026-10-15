
## SDP: The Stable Dependencies Principle

- **Example**
  - Violation of SDP

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_132_0.png)

- The cause of the bad dependency

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_132_1.png)

- Fixing the stability violation using DIP

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_132_2.png)

## SAP: The Stable Abstractions Principle

- Guideline: Use Factories to Reduce Dependency on Concrete Packages

- One way to increase package stability is to reduce its dependency on concrete classes in other packages

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_134_0.png)

## SAP: The Stable Abstractions Principle

- Reduce coupling to a concrete package by using a factory object

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_135_0.png)

## Review: What Is Architecture?

- Software architecture encompasses a set of significant decisions about the organization of a software system.
  - Selection of the structural elements and their interfaces by which a system is composed
  - Behavior as specified in collaborations among those elements
  - Composition of these structural and behavioral elements into larger subsystems
  - Architectural style that guides this organization

## Software Architecture: The “4+1 View” Model

## Logical View

## Implementation View

## Process View

## Deployment View

## Use-Case View

Analysts/Designers
Structure

End-user
Functionality

Programmers
Software management

System integrators
Performance
Scalability
Throughput

System engineering
System topology
Delivery, installation
communication

## Logic View

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_138_0.png)

> Necessary because the Application Layer must have access to the core distribution mechanisms provided with Java RMI

## Process View

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_139_0.png)

## Implementation View (Development View)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_140_0.png)

## Deployment View

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_141_0.png)

Desktop PC : 1

clientComponent

Desktop PC : 2

clientComponent

RegistrationServer

serverComponent

«legacy»

CourseCatalog System

«legacy»

BillingSystem

## Usecase View

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_142_0.png)

## What is An Architectural Pattern?

- An architectural pattern expresses a fundamental structural organization schema for software systems. It provides a set of predefined subsystems, specifies their responsibilities, and includes rules and guidelines for organizing the relationships between them
  - Buschman et al, “Pattern-Oriented Software architecture — A System of Patterns”
- Architectural patterns - Common Architectural Styles
  - Layers
  - Model-view-controller (M-V-C)
  - Pipes and filters
  - Blackboard

## Examples of Architectural Patterns - Layers

- Pattern Name
  - **Layers**
- Context
  - A large system that requires **decomposition**.
- Problem
  - A system which must handle issues at **different levels of abstraction**.
  - For example: hardware control issues, common services issues and domain-specific issues. It would be **extremely undesirable** to write **vertical components that handle issues at all levels**. The same issue would have to be handled (possibly inconsistently) multiple times in different components.

## Examples of Architectural Patterns - Layers

- Forces
  - Parts of the system should be **replaceable**
  - Changes in components should **not ripple**
  - Similar responsibilities should be **grouped together**
  - Size of components – complex components may have to be **decomposed**

- Solution
  - Structure the systems into groups of components that form **layers on top of each other**.
  - Make upper layers use services of the layers below **only** (never above).
  - Try **not** to use services **other than those of the layer directly below** (don’t skip layers unless intermediate layers would only add pass through components).
