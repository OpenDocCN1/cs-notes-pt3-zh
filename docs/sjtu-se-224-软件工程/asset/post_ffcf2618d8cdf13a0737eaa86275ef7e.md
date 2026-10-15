
# Composite Structure Diagram - Collaboration

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_219_0.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_219_1.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_219_2.png)

软件工程概论
Introduction to Software Engineering

## CLASS DESIGN AND UML STATE MACHINE DIAGRAM

## Class Design and UML State Machine Diagram

- Class Design
  - Create Initial Design Classes
  - Define Operations
  - Define Methods
  - Define States
  - Define Attributes
  - Define Dependencies
  - Define Associations
- UML State Machine Diagram

## Class Design Considerations

- Class stereotype
  - Boundary
  - Entity
  - Control
- Applicable design patterns
- Architectural mechanisms
  - Persistence
  - Distribution
  - etc.

## How Many Classes Are Needed?

- **Many, simple classes** means that each class
  - Encapsulates **less** of the overall system intelligence
  - Is **more** reusable
  - Is **easier** to implement
- **A few, complex classes** means that each class
  - Encapsulates a **large** portion of the overall system intelligence
  - Is **less** likely to be reusable
  - Is **more difficult** to implement

A class should have a single well focused purpose. A class should do one thing and do it well!

## Strategies for Designing Entity Classes

- Entity objects are often passive and persistent
- Performance requirements may force some refactoring
- See Identify Persistent Classes step

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_225_0.png)

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_225_1.png)

## Strategies for Designing Control Classes

- What happens to Control Classes?
  - Are they really needed?
  - Should they be split?
- How do you decide?
  - Complexity
  - Change probability
  - Distribution and performance
  - Transaction management

## Operations: Where Do You Find Them?

- Messages displayed in interaction diagrams

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_227_0.png)

- Other implementation dependent functionality
  - Manager functions
  - Need for class copies
  - Need to test for equality

## Name and Describe the Operations

- Appropriate operation names
  - Indicate the outcome
  - Use client perspective
  - Consistent across classes
- Define operation signatures
  - `operationName(parameter : class,...) : returnType`
- Provide short description, including meaning of all parameters

## Guidelines: Designing Operation Signatures

- When designing operation signatures, consider if parameters are:
  - Passed by-value or by-reference?
  - Changed by the operation?
  - Optional?
  - Set to default values?
  - In valid parameter ranges?
- The fewer the parameters, the better
- Pass objects instead of “data bits”

## Operation Visibility

- Visibility is used to enforce encapsulation
- May be public, protected, or private

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_230_0.png)

## How Is Visibility Noted?

The following symbols are used to specify export control:

- **+ Public access**
- **# Protected access**
- **- Private access**

| Class |
|---|
| - privateAttribute |
| # protectedAttribute |
| +publicOp() |
| # protectedOp() |
| - privateOp() |

## Scope

- Determines number of instances of the attribute/operation
  - Instance: one instance for each class instance
  - Classifier: one instance for all class instances
- Classifier scope is denoted by underlining the attribute/operation name

![](img/bd1e40ee9d51e0bf88db831d8e65a09d_232_0.png)

## Example: Scope

<<entity>>
Student
- name
- address
- studentID
- nextAvailID : int
+ addSchedule(theSchedule : Schedule, forSemester : Semester)
+ getSchedule(forSemester : Semester) : Schedule
+ hasPrerequisites(forCourseOffering : CourseOffering) : boolean
# passed(theCourseOffering : CourseOffering) : boolean
+ getNextAvailID() : int
