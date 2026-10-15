
## Architectural Information in the UP Artifacts

- The architectural decisions are recorded in the SAD (Software Architecture Document).
  - This includes the technical memos and descriptions of the architectural views.

## Sample Structure of a SAD

- Architectural Representation
  - **Summary** of how the architecture will be described in this document, such as using the technical memos and the architectural views. This is useful for someone unfamiliar with the idea of technical memos or views. Note that not all views are necessary.
- Architectural Factors and Decisions
  - **Reference** to the Supplementary Specification to view the Factor Table. Also, the set of technical memos that summarize the decisions.
- Logical View
  - UML package diagrams, and class diagrams of major elements. Commentary on the large scale structure and functionality of major components.
- Process View
  - UML class and interaction diagrams illustrating the processes and threads of the system. Group this by threads and processes that interact. Comment on how the interprocess communication works.
- Use-Case View
  - Brief summary of the most architecturally significant use cases. UML interaction diagrams for some architecturally significant use-case realizations, or scenarios, with commentary on the diagrams explaining how they illustrate the major architectural elements.
- Deployment View
  - UML deployment diagrams showing the nodes and allocation of processes and components. Commentary on the networking.
- Data View
  - Overview of the persistent data schema, the schema mapping from objects to persistent data (usually in a relational database), the mechanism of mapping from objects to a database, database stored procedures and triggers.
  - A view onto the UP Data Model, visualized with UML class diagrams used to describe a data model.

## Identify Design Elements

- **Purpose:**
  - To analyze interactions of analysis classes to identify design model elements.
- Identify **Classes**, **Active Classes** and **Subsystems**
- Identify **Subsystem Interfaces**
- Identify and Specify **Events**
- Identify and Specify **Signals**
- In design, **analysis classes evolve into a number of different kinds of design elements**
  - analysis classes represent conceptual things which can perform behavior
  - *classes*
    - to represent a set of rather fine-grained responsibilities;
  - *subsystems*
    - to represent a set of coarse-grained responsibilities, perhaps composed of a further set of subsystems, but ultimately a set of classes;
  - *active classes*
    - to represent threads of control in the system;
  - *interfaces*
    - to represent abstract declarations of responsibilities provided by a class or subsystem.
- In addition, in design we shall also identify
  - *events*
    - which are specifications of **interesting occurrences in time and space** that usually (if they are noteworthy) **require some response from the system**; and
  - *signals*
    - to represent **asynchronous mechanisms** used to communicate certain types of events within the system.
- Events and the Signals that are used to communicate them, allow us to describe the asynchronous triggers of behavior to which the system must respond.

## 软件工程概论
Introduction to Software Engineering

## SUBSYSTEM DESIGN

## Subsystem Design Overview

Design Subsystems and Interfaces  
Use-Case Realization  
Design Guidelines  
Subsystem Design  
Design Subsystems and Interfaces (updated)  
Use-Case Realization (updated)  
Design Classes

## Subsystem Design - Purpose

- To define the behaviors specified in the subsystem's interfaces in terms of collaborations of contained classes
- To document the internal structure of the subsystem
- To define realizations between the subsystem's interfaces and contained classes
- To determine the dependencies upon other subsystems
