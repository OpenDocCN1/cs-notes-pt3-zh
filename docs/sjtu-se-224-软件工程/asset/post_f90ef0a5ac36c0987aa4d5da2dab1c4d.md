
## Dependencies vs. Associations

- Associations are structural relationships
- Dependencies are non-structural relationships
- In order for objects to “know each other” they must be visible

- Local variable reference
- Parameter reference
- Global reference
- Field reference

Dependency

Association

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_252_0.png)

## Associations vs. Dependencies in Collaborations

- An instance of an association is a link
  - All links become **associations** unless they have global, local or parameter visibility
  - Context dependent relationship
- Dependencies are **transient** links
  - Have a limited duration
  - Context independent relationship
  - Summary relationship

## Identifying Dependencies: Considerations

- **Permanent** relationships - **Association** (field visibility)
- **Transient** relationships - **Dependency**
  - **Multiple objects share the same instance**
    - Pass instance as a parameter (parameter visibility)
    - Make instance a managed global (global visibility)
  - **Multiple objects don’t share the same instance** (local visibility)
- How long does it take to create/destroy?
  - **Expensive?** Use field, parameter, or global visibility
  - Strive for the lightest relationships possible

## Example: Define Dependencies (before)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_255_0.png)

## Example: Define Dependencies (after)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_256_0.png)

Global visibility

Field visibility

## Define Associations

- Purpose
  - Refine remaining associations
- Things to look for :
  - Association vs. Aggregation
  - Aggregation vs. Composition
  - Attribute vs. Association
  - Navigability
  - Association class design
  - Multiplicity design

## What is Composition?

- A form of aggregation with strong ownership and coincident lifetimes
  - The parts **cannot** survive the whole/aggregate

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_258_0.png)

## Aggregation: Shared Vs. Non-shared

### ◆ Shared Aggregation

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_259_0.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_259_1.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_259_2.png)

By definition, composition is non-shared aggregation

## Example: Composition

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_261_0.png)

## Attributes Vs Composition

- Use composition when
  - Properties need independent identities
  - Multiple classes have the same properties
  - Properties have a complex structure and properties of their own
  - Properties have complex behavior of their own
  - Properties have relationships of their own
- Otherwise use attributes

## Example: Attributes Vs Composition

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_263_0.png)

Student

- name
- address
- <<classifier scope>> - nextAvailID : int
- StudentID : int
- dateofBirth : Date

- + addSchedule()
- + getSchedule()
- + delete schedule()
- + hasPrerequisites()
- # passed()

Schedule

- Semester

- + submit()
- + // save()
- # any conflicts?()
- + // create with offerings()
- + new()
- + passed()

Attributes

Composition of separate class

## Navigability: Which Directions Are Really Needed?

- Explore interaction diagrams
- Even when both directions seem required, one may work
  - Navigability in one direction is infrequent
  - Number of instances of one class is small

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_264_0.png)

## Association Class

- A class “attached” to an association
- Contains properties of a relationship
- One instance per link

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_265_0.png)

## Example: Association Class Design

Design Decisions

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_266_0.png)
