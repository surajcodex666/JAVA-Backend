# Spring Boot
- Spring Boot is one approach to develop Spring Based Application with less configurations.
    - Spring Boot = Spring Framework - Xml Configuration
- Spring Boot is not replacement for Spring Framework. It is developed on top of Spring Framework   

### NOTE - All Spring Framework concepts can be used in Spring boot also

## Advantages -
1) Less Configuration 
    - No need to write XML files, no need to start IOC container all will be done automatically
2) Pom Starters
    - ex: web-starter, jpa-starter[database], security-starter, mail-starter
3) Auto Configuration    
4) Embedded Servers
    - ex: Tomcat(default), Jetty, Netty
5) Actuators (provides production ready features)

### NOTE - The latest stable version of Spring Boot is 4.1.x (specifically 4.1.0), which requires Java 17 as a minimum version and supports up to Java 26.

## Spring Boot Application Creation
- We can create Boot Aplication in 2 ways 
            1) Intializer website(start.spring.io)
            2) Spring Starter Project in IDE
### NOTE -
- If we try to create boot application using IDE then internally IDE will communicate with Initializer Website to create the project
- Internet connection is mandatory for system to create Spring Boot Application

## Spring Boot Folder Structure
- src/main/java : To keep our source code 

        1) it has Application.java : It is the start class of Spring Boot(main class)

- src/main/resources : To keep Project configuration files

        1) application.properties/yml

- src/test/java : to keeo JUnit code(unit testing)

        1) ApplicationTest.java

- src/test/resources : Unit Testing related config files goes here
- Maven dependencies : Downloaded jars will be available   
- pom.xml : Maven Configuration file (dependencies)    

## Spring Boot Start Class
The Spring Boot Start Class is the entry point of a Spring Boot application.

```java
@SpringBootApplication
public class SpringBootAppApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootAppApplication.class, args);
    }
}
```
## @SpringBootApplication
Combines:
- @SpringBootConfiguration
- @EnableAutoConfiguration
- @ComponentScan

### @SpringBootConfiguration
- Marks the class as a configuration class.

### @EnableAutoConfiguration
- Automatically configures Spring Boot based on project dependencies.

### @ComponentScan
- Scans the current package and sub-packages for:
  - @Component
  - @Service
  - @Repository
  - @Controller
  - @RestController

## main() Method
- Entry point of the Java application.
- JVM starts execution here.

## SpringApplication.run()
- Spring Boot start class main() method will call SpringApplication.run() method
- It is the entry point for boot application execution
- This run() method will return reference of IOC

```java
SpringApplication.run(SpringBootAppApplication.class, args);
```

Responsibilities:
- Creates ApplicationContext (IoC Container)
- Scans components
- Creates Beans
- Performs Dependency Injection
- Applies Auto Configuration
- Starts embedded Tomcat (if spring-boot-starter-web is present)

