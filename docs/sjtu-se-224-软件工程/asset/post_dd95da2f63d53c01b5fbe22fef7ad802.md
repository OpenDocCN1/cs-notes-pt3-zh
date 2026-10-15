
## Software Engineering
## Appendix1 UML C++ Map
## Associations
- Bi-directional associations
## Association Navigability
- Uni-directional associations
## Association Roles
## Association Multiplicity
## Association Class
## Reflexive Associations
A1 - 2

## Software Engineering
## Appendix2 UML Java Mapping
## 软件工程
Appendix: UML to Java Mapping
## Class Scope Attributes and Operations
## Mapping Representation: Notes
## Utility Class
## Visibility for Attributes and Operations
## Nested Class
A2 - 1

## Software Engineering
## Appendix2 UML Java Mapping
## Aggregation
## Generalization
## Composition
## Multiple Inheritance
## Interfaces and Realizes Relationships
## Multiple Inheritance (continued)
A2 - 3

## Abstract Class
Animal (abstract)
+talk() {abstract}
Lion
+talk()
Tiger
+talk()
abstract class Animal
public abstract void talk();
class Tiger extends Animal
public Tiger() {}
public void talk() {}

## Parameterized Class
Java does not support parameterized classes
Set
T, int
insert(T)
remove(T)
<<binds>>
<float, 100>
mySetOfFloats

## Subsystems
ICourseCatalog
<<subsystem>>
CourseCatalog
package CourseCatalog;
public interface ICourseCatalog {
public CourseOfferingList getCourseOfferings();
}

gb1 Should this note be deleted along with the related code (getCourseOfferings() : CourseOfferingList)?
gbastoky, 2004-6-18

## 软件工程
Appendix: UML to VB Mapping
## Class Scope Attributes and Operations
Student
- nextAvailID : Integer = 1
+ getNextAvailID() : Integer

Visual Basic does not support the semantics of attributes or operations with class scope (i.e. static)

## Mapping Representation: Notes
Course

Notes will be used in the rest of the presentation to contain Visual Basic code for the attached UML elements

```
' Course.cls - class module filename
Private Sub Class_Initialize()
End Sub
Private Sub Class_Terminate()
End Sub
```

## Utility Class
- A grouping of global attributes and operations
<<Utility>>
MathPack
- randomSeed : long = 0
Pi : double = 3.14159265358979
+ sin (angle : double) : double
+ cos (angle : double) : double
+ random() : double

Classes with the <<Utility>> stereotype have no corresponding semantics in Visual Basic.

## Visibility for Attributes and Operations
Student
- name : String
+ addSchedule (thisSchedule : Schedule, forSemester : Semester)
# addPrereq (thisPrereq : CourseOffering) : Integer
# passed (thisCourseOffering : CourseOffering) : Integer

```
' Student.cls - class module filename
Private name as String
Public Sub addSchedule(thisSchedule as Schedule, forSemester as Semester)
End Sub
Public Function addPrereq(thisPrereq as CourseOffering) as Integer
End Function
Private Function passed(thisCourseOffering as CourseOffering) as Integer
End Function
```

## Nested Class
- Hide a class that is relevant only for implementation
Outer
Outer.Inner

Visual Basic does not support nested classes.

## Software Engineering
## Appendix3 UML VB Mapping
## Associations
- Bi-directional associations
## Association Multiplicity
## Association Navigability
- Uni-directional associations
## Association Class
## Association Roles
## Reflexive Associations
A3 - 2

## Interfaces and Realizes Relationships
<<Interface>> Serializable
* Serializable.cls
<<entity>> Schedule
* Schedule.cls
Implements Serializable

## Subsystems
Visual Basic does NOT directly support subsystems
ICourseCatalog
<<subsystem>> CourseCatalog
