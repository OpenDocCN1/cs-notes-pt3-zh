
# HelloWorld RESTful Web Service
- Deploy to Tomcat

## Project Deployments

## Manage Deployments
Deploy and undeploy J2EE projects.

Project: HelloWorld

## Deployments
HelloWorld

Deployment Status

## New Deployment
Create new project deployment for HelloWorld

Web Project: HelloWorld

Server: MyEclipse Tomcat

Edit server connectors...

Deploy type: Exploded Archive (development mode) Packaged Archive (production mode)

Deploy Location: D:\SOA\.metadata\.me_tcat\webapps\HelloWorld

MyEclipse Tomcat

Finish Cancel

# HelloWorld RESTful Web Service
- Test
  - type in
  http://localhost:8080/HelloWorld/services/helloworld

Hello World

Successful

## Tools in MyEclipse

## JAX-RS Resource Method

## New JAX-RS Resource Method
Create a new JAX-RS resource method

Method name: sayHiWithName

Return type: String

HTTP method: GET

URL path: /{name}

Consumes: <unspecified>

Produces: text/plain

## Method parameters:

| Java Type | Java Name | Param Type | Param Name | Default Value |
| String | name | PathParam | name | |

Method signature preview:

```
@GET @Path("/{name}")
@Produces("text/plain")
public String sayHiWithName(@PathParam("name") String name);
```

Finish
Cancel

## Path Parameter Example

```
@GET
@Path("/{name}")
@Produces("text/plain")
public String sayHiWithName(@PathParam("name") String name) {
    return "Hi, " + name;
}
```

## Annotations
- @Path
  - URL Path
- @GET / @POST
  - HTTP Method
- @Consumes
  - MIME type the resource can accept from client (for POST)
- @Produces
  - MIME type the resource can produce (send back to client)

```
//set URL
URL url = new URL("http://localhost:8080/HelloWorld/services/helloworld/xml");

//make connection
URLConnection urlc = url.openConnection();

//use GET mode
urlc.setDoInput(true);
urlc.setAllowUserInteraction(false);

//get result
BufferedReader br = new BufferedReader(new InputStreamReader(urlc.getInputStream()));

String l = null;
while ((l = br.readLine()) != null) {
    System.out.println(l);
}
br.close();
```

## Test with REST WS Explorer

## REST Web Services Explorer
WADL URL http://localhost:8080/HelloWorld/services/application.wadl

HelloWorld > helloworld > hi

Resource: helloworld/hi
(http://localhost:8080/HelloWorld/services/helloworld/hi)

Choose method to test: GET(text/plain)

Test
- HelloWorld
  - helloworld
    - hi
    - {name}

## Java API for XML Web Services
(JAX-WS)

- JAX-WS is a Java programming language API for creating web services.
- Latest version JAX-WS 2.0
- Part of Java EE.
- New in Java SE 6.
- API stack for web services.
- Replaces JAX-RPC.
- **JAXM** (JAVA API For XML Message)
- **SAAJ** (SOAP With Attachment API For Java)
- **JAX-RS**

## Writing A Web Service with JAX-WS

```
package loanservice;

import javax.jws.WebService;
import javax.jws.WebMethod;
import javax.xml.ws.Endpoint;

@WebService
public class LoanApprover {
    @WebMethod
    public boolean approve(String name) {
        return name.equals("Mike");
    }
    public static void main(String[] args){
        LoanApprover la = new LoanApprover();
        Endpoint endpoint =
            Endpoint.publish("http://localhost:8080/loanservice", la);
    }
}
```
