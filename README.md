# SoapProject

## Overview

SoapProject is a practical demonstration of implementing a SOAP web service using Spring Boot and Apache CXF. The project involves managing bank account entities (`Compte`) through a web service interface. This implementation demonstrates the use of JPA for data persistence and includes features such as creating, retrieving, updating, and deleting bank accounts.

## Features

- **SOAP Web Service**: Implemented using JAX-WS and Apache CXF.
- **Entity Management**: CRUD operations for `Compte` entities with attributes such as `solde`, `type`, and `dateCreation`.
- **Spring Boot Integration**: Leverages Spring Boot for a simplified development process.
- **In-Memory Database**: Uses H2 database for temporary data storage during development.
- **WSDL Generation**: Automatically generates WSDL for service description.
- **Testing with SoapUI**: Provides detailed instructions for testing SOAP methods using SoapUI.

## Project Structure

SoapProject ├── src/main/java/com/example/demo │ ├── config # Apache CXF configuration │ ├── entities # JPA entity definitions (e.g., Compte) │ ├── repositories # Spring Data JPA repositories │ ├── ws # SOAP web service implementations │ └── DemoApplication.java # Main Spring Boot application ├── src/main/resources │ ├── application.properties # Configuration properties └── pom.xml # Maven dependencies

php
Copy code

## Dependencies

The project relies on the following Maven dependencies:

```xml
<dependencies>
    <!-- Apache CXF Core for SOAP support -->
    <dependency>
        <groupId>org.apache.cxf</groupId>
        <artifactId>cxf-core</artifactId>
        <version>4.0.2</version>
    </dependency>

    <!-- Apache CXF Starter for JAX-WS with Spring Boot -->
    <dependency>
        <groupId>org.apache.cxf</groupId>
        <artifactId>cxf-spring-boot-starter-jaxws</artifactId>
        <version>4.0.2</version>
    </dependency>
</dependencies>
Configuration
Database Configuration
Configure the H2 database in application.properties:

properties
Copy code
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
Apache CXF Endpoint
Configure the SOAP endpoint in CxfConfig.java:

java
Copy code
@Configuration
@AllArgsConstructor
public class CxfConfig {
    private final Bus bus;
    private final CompteSoapService compteSoapService;

    @Bean
    public EndpointImpl endpoint() {
        EndpointImpl endpoint = new EndpointImpl(bus, compteSoapService);
        endpoint.publish("/ws");
        return endpoint;
    }
}
Running the Project
Clone the repository:

bash
Copy code
git clone https://github.com/Elansari-Jaafar/SoapProject.git
cd SoapProject
Build and run the application:

bash
Copy code
mvn spring-boot:run
Access the WSDL: Open a browser and navigate to:

bash
Copy code
http://localhost:8080/ws?wsdl
Testing the Service
Use SoapUI for testing SOAP endpoints.
Example methods to test:
getComptes: Retrieve all accounts.
getCompteById: Retrieve an account by its ID.
createCompte: Create a new account with initial solde and type.
deleteCompte: Delete an account by its ID.
Author
Elansari Jaafar
GitHub Profile

License
This project is licensed under the MIT License. See the LICENSE file for details.

javascript
Copy code

Copy and save this content as `README.md` in your project's root directory.
