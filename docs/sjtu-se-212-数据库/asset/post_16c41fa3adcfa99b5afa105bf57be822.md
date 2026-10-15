
## JDBC

- JDBC is a Java API for communicating with database systems supporting SQL.
- JDBC supports a variety of features for querying and updating data, and for retrieving query results.
- JDBC also supports metadata retrieval, such as querying about relations present in the database and the names and types of relation attributes.
- Model for communicating with the database:
  - Open a connection
  - Create a “statement” object
  - Execute queries using the Statement object to send queries and fetch results
  - Exception mechanism to handle errors

## SQLCA

## SQL Communication Area

- is an area of memory that is used on every database request for communicating statistics and errors from the application to the database server and back to the application.
- The SQLCA is used as a handle for the application-to-database communication link. It is passed in to all database library functions that need to communicate with the database server. It is implicitly passed on all embedded SQL statements.

## SQLCA Fields

- **sqlcode** A 32-bit integer that specifies the error code when the database detects an error on a request.
- Definitions for the error codes can be found in the header file `sqlerr.h`.
  - The error code is 0 (zero) for a successful operation
  - 100 for row not found
  - Positive for a warning
  - Negative for an error.

![](img/5285b20d8f5a79969a3f150d38beebfc_137_0.png)

## Chapter 7: Entity-Relationship Model

## Chapter 7: Entity Relationship Model

- Design Process
- Modeling
- Constraints
- E-R Diagram
- Design Issues
- Weak Entity Sets
- Extended E-R Features
- Design of the Bank Database
- Reduction to Relation Schemas
- Database Design
- UML

## Modeling

- A *database* can be modeled as:
  - a collection of entities,
  - relationship among entities.
- An *entity* is an object that exists and is distinguishable from other objects.
  - Example: specific person, company, event, plant
- Entities have *attributes*
  - Example: people have names and addresses
- An *entity set* is a set of entities of the same type that share the same properties.
  - Example: set of all persons, companies, trees, holidays

## Entity Sets instructor and student

| instructor_ID | instructor_name |
|---|---|
| 76766 | Crick |
| 45565 | Katz |
| 10101 | Srinivasan |
| 98345 | Kim |
| 76543 | Singh |
| 22222 | Einstein |

instructor

| student-ID | student_name |
|---|---|
| 98988 | Tanaka |
| 12345 | Shankar |
| 00128 | Zhang |
| 76543 | Brown |
| 76653 | Aoi |
| 23121 | Chavez |
| 44553 | Peltier |

student

## Relationship Set advisor

![](img/5285b20d8f5a79969a3f150d38beebfc_142_0.png)

instructor

student

## Relationship Sets (Cont.)

- An *attribute* can also be property of a relationship set.
- For instance, the *advisor* relationship set between entity sets *instructor* and *student* may have the attribute *date* which tracks when the student started being associated with the advisor

![](img/5285b20d8f5a79969a3f150d38beebfc_143_0.png)

## Degree of a Relationship Set

- **binary relationship**
  - involve two entity sets (or degree two).
  - most relationship sets in a database system are binary.
- Relationships between more than two entity sets are rare. Most relationships are binary. (More on this later.)
  - Example: students work on research projects under the guidance of an instructor.
  - relationship proj_guide is a ternary relationship between instructor, student, and project

## Attributes

- An entity is represented by a set of attributes, that is descriptive properties possessed by all members of an entity set.
- Example:
  - instructor = (ID, name, street, city, salary)
  - course = (course_id, title, credits)

Domain – the set of permitted values for each attribute

Attribute types:

Simple and composite attributes.

Single-valued and multivalued attributes

Example: multivalued attribute: phone_numbers

Derived attributes

Can be computed from other attributes

Example: age, given date_of_birth
