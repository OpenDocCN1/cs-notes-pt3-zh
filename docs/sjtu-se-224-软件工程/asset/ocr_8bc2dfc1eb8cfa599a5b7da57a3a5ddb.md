# Modeling Convention: Subsystems and Interfaces

<<subsystem>> package

<<subsystem>>
CourseCatalogSystem

ICourseCatalogSystem

Interfaces start with an "I"

<<subsystem proxy>> class

ICourseCatalogSystem
getCourseOfferings(forSemester : Semester, forStudent : Student) : CourseOfferingList
initialize()

<<subsystem proxy>>
CourseCatalogSystem
getCourseOfferings()
initialize()