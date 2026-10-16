
## JAVA SERVER PAGES (JSP)

+   A JSP page with embedded Java code

```
<html>
<head> <title> Hello </title> </head>
<body>
<% if (request.getParameter("name") == null)
{ out.println("Hello World"); }
else { out.println("Hello, " + request.getParameter("name")); }
%>
</body>
</html>
```

+   JSP is compiled into Java + Servlets

+   JSP allows new tags to be defined, in tag libraries

+   such tags are like library functions, can be used for example to build rich user interfaces such as paginated display of large datasets

## PHP

-   PHP is widely used for Web server scripting
-   Extensive libraries including for database access using ODBC

```
<html>
<head> <title> Hello </title> </head>
<body>
<?php if (!isset($_REQUEST['name']))
{ echo "Hello World"; }
else { echo "Hello, " . $_REQUEST['name']; }
?>
</body>
</html>
```

## Client Side Scripting

-   Browsers can fetch certain scripts (client-side scripts) or programs along with documents, and execute them in “safe mode” at the client site
-   Javascript
-   Macromedia Flash and Shockwave for animation/games
-   VRML
-   Applets

-   Client-side scripts/programs allow documents to be active
-   E.g., animation by executing programs at the local site
-   E.g., ensure that values entered by users satisfy some correctness checks
-   Permit flexible interaction with the user.
-   Executing programs at the client site speeds up interaction by avoiding many round trips to server

## Client Side Scripting and Security

-   Security mechanisms needed to ensure that malicious scripts do not cause damage to the client machine
-   Easy for limited capability scripting languages, harder for general purpose programming languages like Java

-   E.g., Java’s security system ensures that the Java applet code does not make any system calls directly
-   Disallows dangerous actions such as file writes
-   Notifies the user about potentially dangerous actions, and allows the option to abort the program or to continue execution.

## JAVASCRIPT

-   Javascript very widely used
-   forms basis of new generation of Web applications (called Web 2.0 applications) offering rich user interfaces
-   Javascript functions can
-   check input for validity
-   modify the displayed Web page, by altering the underlying **document object model (DOM)** tree representation of the displayed HTML text
-   communicate with a Web server to fetch data and modify the current page using fetched data, without needing to reload/refresh the page
-   forms basis of AJAX technology used widely in Web 2.0 applications
-   E.g. on selecting a country in a drop-down menu, the list of states in that country is automatically populated in a linked drop-down menu

## JAVASCRIPT

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_394_0.png)

+   Example of Javascript used to validate form input

```
<html> <head>
<script type="text/javascript">
function validate() {
var credits=document.getElementById("credits").value;
if (isNaN(credits)|| credits<=0 || credits>=16) {
alert("Credits must be a number greater than 0 and less than 16");
return false
}
}
</script>
</head> <body>
<form action="createCourse" onsubmit="return validate()">
Title: <input type="text" id="title" size="20"><br />
Credits: <input type="text" id="credits" size="2"><br />
<Input type="submit" value="Submit">
</form>
</body> </html>
```

## Application Architectures

## APPLICATION ARCHITECTURES

-   Application layers
-   Presentation or user interface
-   model-view-controller (MVC) architecture
-   **model**: business logic
-   **view**: presentation of data, depends on display device
-   **controller**: receives events, executes actions, and returns a view to the user
-   **business-logic** layer
-   provides high level view of data and actions on data
-   often using an object data model
-   hides details of data storage schema
-   **data access** layer
-   interfaces between business logic layer and the underlying database
-   provides mapping from object model of business layer to relational model of database

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_396_0.png)
