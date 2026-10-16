
## Information in a View-1

+   1. Primary presentation (a diagram, table, or outline)
+      - If graphical, always include a key or a reference that explains the notation.
+   2. Element catalog
+      - Prose description of the elements in the primary presentation
+      - Include elements that are external to the scope of that view
+      - Software interfaces of the elements (or incorporate the interface specifications by reference)
+      - Behavior of the element. Document this with, for example, sequence diagrams or statecharts.

## Information in a View-2

+   3. Other information
+      - Driving architectural requirements
+      - Rationale for design decisions (including rejected alternatives)
+      - Results of analysis, prototypes, and experiments that provide evidence that architecture is fit for purpose
+      - Variability mechanisms built in to the architecture—maybe this architecture is a reference architecture. Points where the architecture can be parameterized (e.g., number of instances in a pool)
+      - Places where elements can be replicated, omitted, or replaced
+      - Context diagram showing the relationship of software elements to external entities

## Documentation Beyond Views-1

+   1. Documentation roadmap
+      - Explains how the documentation is organized to help stakeholders do their job
+      - Explains the views that were chosen and why
+   2. System overview
+      - Prose description of the system and its purpose, functionality, major external interfaces, and major quality attributes.
+      - Its goal is to provide context for new project members.
+      - It may point to overview elsewhere if one exists in the overall system documentation.

## Documentation Beyond Views-2

+   3. Architecturally significant requirements
+      - may refer to a separate requirements document
+      - Three kinds of requirements
+        - functional requirements (as use cases, for example)
+        - quality attribute requirements (as scenarios, for example)
+        - design constraints; for example, “the system shall be developed using J2EE.”
+   4. System overview
+      - tables showing how elements in one view correspond to elements in another view
+      - Modules mapping to modules
+      - Modules mapping to components and connectors

## Documentation Beyond Views-3

+   5. Architecture analysis and rationale
+      - Major architectural approaches taken
+      - Documented design decisions (including rejected alternatives)
+      - If architecture evaluation was performed, the results could go here.
+   6. Mapping architecture to requirements
+      - shows how each requirements is satisfied by one or more elements of the architecture or an architectural approach

## Module Summary-1

Primary uses of architecture documentation include construction, education, and analysis. Documenting an architecture is a matter of documenting its views, and then documenting information that applies to more than one view. A view is a representation of a structure. There are three kinds of architectural views:

1. Module views
2. C&C views
3. Allocation views

## Module Summary-2

Diagrams are not enough! The elements in diagrams must be explained.

Views by themselves are not enough! The views must be augmented with an explanation of the documentation organization and the system as a whole.

## Views

Section 1: Primary Presentation of the View

Section 2: Element Catalog
Section 2.A: Elements and their properties
Section 2.B: Element catalog
Section 2.C: Element behavior

Section 3: Context Diagram

Section 4: Variability Guide

Section 5: Architecture Background
Section 5.0: Design rationale
Section 5.1: Analysis of results

Section 6: Glossary of Terms

Section 7: Other Information

## Figure 9.2: The nine parts of interface documentation

Section 2C: Element Interface Specification

+   Section 2.C.1: Interface Identity
+   Section 2.C.2: Resources provided
+   Section 2.C.3: Resource syntax
+   Section 2.C.4: Resource semantics
+   Section 2.C.5: Resource usage restrictions

+   Section 2.C.3: Locally defined data types
+   Section 2.C.4: Exception definitions
+   Section 2.C.5: Variability provided
+   Section 2.C.6: Quality attribute characteristics
+   Section 2.C.7: Element requirements
+   Section 2.C.8: Rationale and design issues
+   Section 2.C.9: Usage guide

## Figure 9.3: Summary of cross-view documentation

Documentation across Views

How the document is organized:
1.1 View catalog
1.2 View template

What the architecture is:
2.1 System overview
2.2 Mapping between views
2.3 List of elements and where they appear
2.4 Project glossary

Why the architecture is the way it is:
3.1 Rationale
