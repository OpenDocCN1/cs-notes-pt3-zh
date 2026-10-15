# Key Layers

| Layer Name | Responsibilities | Implementation Technology |
|---|---|---|
| Presentation | User Interface | JSP/HTML/JavaScript, Java.awt.Component subclasses |
| Application | Use-case UI workflow, syntactic validation, interaction with services | Servlets, <usebean> targets, Java.awt.Panel subclasses |
| Services | Controlling txns, business/ workflow logic, acting as facade | EJB Session Beans |
| Domain | The domain model, domain/ business logic, semantic validation | EJB Entity Beans, Plain Old Java Objects, |
| Persistence | Persistent storage of domain object state | O/R mappers, OODBMS, EJB Entity Bean BMP/CMP |

type dependency

UI Layers