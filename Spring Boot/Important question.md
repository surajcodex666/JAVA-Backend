# Spring Boot Interview Notes - Part 1

> **Target Audience:** Freshers & Experienced Developers
>
> **Interview Level:** Beginner → Intermediate
>
> **Spring Boot Version:** 3.x

---

# 1. What is Spring Boot?

## Interview Definition

**Spring Boot is an extension of the Spring Framework that simplifies the development of Java applications by providing auto-configuration, embedded servers, starter dependencies, and production-ready features.**

In simple words,

> Spring Boot helps developers create Spring applications quickly with very little configuration.

---

## Why was Spring Boot introduced?

Before Spring Boot,

Developers had to

- Configure XML files
- Configure DispatcherServlet
- Configure View Resolver
- Configure DataSource
- Configure Tomcat
- Add every dependency manually

This consumed a lot of time.

Spring Boot automates all these configurations.

---

## Features

- Auto Configuration
- Embedded Tomcat/Jetty/Undertow
- Starter Dependencies
- Production Ready Features
- Actuator
- Spring Initializr Support
- Minimal Configuration
- Microservices Support

---

## Example

Without Spring Boot

```java
100+ lines of configuration
```

With Spring Boot

```java
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {

        SpringApplication.run(DemoApplication.class,args);

    }

}
```

That's enough to start the application.

---

## Advantages

- Less Configuration
- Faster Development
- Embedded Server
- Easy Dependency Management
- Production Ready
- Easy Testing

---

## Interview Questions

### What is Spring Boot?

Spring Boot is an extension of Spring Framework that simplifies application development using auto configuration, starter dependencies and embedded servers.

---

### Is Spring Boot a replacement for Spring?

No.

Spring Boot is built on top of the Spring Framework.

Spring Boot uses Spring internally.

---

### Can Spring Boot work without Spring?

No.

Spring Boot depends on the Spring Framework.

---

# 2. Spring Boot Version History

## Why should we know it?

Interviewers ask this to check whether you know the ecosystem.

---

## Timeline

### Spring Boot 1.x

Released in 2014

Features

- Initial release
- Embedded Tomcat
- Auto Configuration

---

### Spring Boot 2.x

Released in 2018

New Features

- Better performance
- Spring 5 support
- Reactive Programming
- WebFlux
- Improved Actuator

---

### Spring Boot 3.x

Released in 2022

Major Changes

- Java 17 Minimum
- Jakarta EE
- Spring Framework 6
- Better Native Image Support
- Better Performance

---

## Interview Point

Spring Boot 3.x uses

```text
jakarta.*
```

instead of

```text
javax.*
```

Example

Old

```java
import javax.persistence.Entity;
```

New

```java
import jakarta.persistence.Entity;
```

---

## Current Recommendation

Always use

- Java 17+
- Spring Boot 3.x

---

# 3. Advantages of Spring Boot

## Main Advantages

### 1. Auto Configuration

Spring automatically configures beans.

Example

Instead of configuring DataSource manually,

Spring Boot creates it automatically.

---

### 2. Starter Dependencies

Instead of adding many dependencies,

Add

```xml
spring-boot-starter-web
```

and all required libraries are downloaded automatically.

---

### 3. Embedded Server

No external Tomcat installation.

Supported

- Tomcat
- Jetty
- Undertow

---

### 4. Production Ready

Provides

- Monitoring
- Health Check
- Metrics
- Logging

through Spring Boot Actuator.

---

### 5. Faster Development

Less code

Less XML

Less configuration

---

### 6. Easy Testing

Supports

- JUnit
- Mockito
- Spring Test

---

## Interview Answer

Spring Boot reduces development time by providing auto configuration, starter dependencies, embedded servers and production-ready features.

---

# 4. Spring Boot Application Creation

## Ways to Create

### Method 1

Spring Initializr

https://start.spring.io

Most Recommended

---

### Method 2

IntelliJ IDEA

New Project

↓

Spring Initializr

---

### Method 3

Spring Tool Suite (STS)

---

## Required Information

- Project Type
- Maven/Gradle
- Java Version
- Group ID
- Artifact ID
- Package Name
- Dependencies

---

## Common Dependencies

```text
Spring Web
Spring Data JPA
MySQL Driver
Lombok
Validation
Spring Security
Actuator
DevTools
```

---

## Generated Project

```
DemoProject
│
├── src
├── pom.xml
├── mvnw
├── mvnw.cmd
└── target
```

---

# 5. Spring Boot Folder Structure

```
DemoProject
│
├── src
│
├── main
│   │
│   ├── java
│   │      └── Java Source Code
│   │
│   └── resources
│          │
│          ├── application.properties
│          ├── static
│          ├── templates
│          └── banner.txt
│
├── test
│
├── pom.xml
│
└── target
```

---

## Important Folders

### src/main/java

Contains Java source files.

---

### src/main/resources

Contains

- application.properties
- Static Files
- HTML Templates

---

### src/test

Contains unit tests.

---

### pom.xml

Contains dependencies.

---

### target

Compiled classes and JAR files.

---

## Interview Point

Never modify

```text
target
```

It is generated automatically.

---

# 6. What is Start Class?

## Definition

The Start Class is the main class from which the Spring Boot application starts.

Example

```java
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {

        SpringApplication.run(DemoApplication.class,args);

    }

}
```

---

## Responsibilities

- Starts Spring Boot
- Creates IoC Container
- Performs Component Scan
- Enables Auto Configuration
- Starts Embedded Server

---

## Interview Point

There should generally be **one** start class in a Spring Boot application.

It should be placed in the **root package** so that component scanning can discover all sub-packages.

---

# 7. What is @SpringBootApplication?

## Definition

`@SpringBootApplication` is the main annotation used to start a Spring Boot application.

It is a combination of three annotations.

```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```

---

## @SpringBootConfiguration

Marks the class as a Spring Boot configuration class.

---

## @EnableAutoConfiguration

Automatically configures Spring Beans based on dependencies available on the classpath.

Example

If

```xml
spring-boot-starter-web
```

is added,

Spring Boot automatically configures

- Tomcat
- DispatcherServlet
- Jackson
- MVC

---

## @ComponentScan

Scans the package and sub-packages for Spring Beans.

---

## Example

```java
@SpringBootApplication
public class DemoApplication {

}
```

Equivalent to

```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
public class DemoApplication {

}
```

---

## Interview Question

### Can we use these three annotations separately?

Yes.

`@SpringBootApplication` is simply a convenience annotation that combines all three.

---

# 8. What is Component Scanning?

## Definition

Component Scanning is the process in which Spring searches for classes annotated with stereotype annotations and registers them as Spring Beans.

---

## Stereotype Annotations

- @Component
- @Service
- @Repository
- @Controller
- @RestController

---

## Example

```java
@Service
public class StudentService {

}
```

Spring automatically creates an object of this class.

---

## Default Scanning

Spring scans

- Current package
- All sub-packages

---

Example

```
com.demo

│

├── controller

├── service

├── repository

└── DemoApplication
```

Everything is scanned.

---

## If the Bean is Outside the Package?

Use

```java
@ComponentScan("com.company")
```

or

```java
@ComponentScan(basePackages={
"com.company.service",
"com.company.repository"
})
```

---

## Interview Questions 

### What is Component Scanning?

It is the process through which Spring automatically detects classes annotated with stereotype annotations and registers them as beans in the IoC container.

---

### Which annotation performs Component Scanning?

```java
@ComponentScan
```

or indirectly

```java
@SpringBootApplication
```

---

### Which annotations are discovered?

- @Component
- @Service
- @Repository
- @Controller
- @RestController

---

# ⭐ Frequently Asked Interview Questions (Part 1)

### Q1. What is Spring Boot?

Extension of Spring Framework that simplifies development.

---

### Q2. Is Spring Boot a replacement for Spring?

No.

It is built on top of Spring Framework.

---

### Q3. Which Java version is required for Spring Boot 3?

Java 17 or higher.

---

### Q4. Which annotation starts a Spring Boot application?

`@SpringBootApplication`

---

### Q5. What are the three annotations inside `@SpringBootApplication`?

- `@SpringBootConfiguration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

---

### Q6. Which embedded servers does Spring Boot support?

- Tomcat
- Jetty
- Undertow

---

### Q7. What is Component Scanning?

Automatic detection and registration of Spring Beans.

---

### Q8. Which package is scanned by default?

The package containing the Start Class and all its sub-packages.

---

# 🚀 One-Minute Revision

- Spring Boot = Simplified Spring Framework.
- Spring Boot provides Auto Configuration, Starter Dependencies, Embedded Servers.
- Spring Boot 3.x requires Java 17+.
- Main class is called the Start Class.
- `@SpringBootApplication` = `@SpringBootConfiguration` + `@EnableAutoConfiguration` + `@ComponentScan`.
- Component Scanning finds classes annotated with `@Component`, `@Service`, `@Repository`, `@Controller`, and `@RestController`.
- Keep the Start Class in the root package for proper component scanning.
- Use Spring Initializr to create new Spring Boot projects quickly.

# Spring Boot Interview Notes - Part 2

> **Interview Level:** Beginner → Intermediate
>
> **Spring Boot Version:** 3.x

---

# 9. What is Base Package Naming Convention?

## Interview Definition

The **Base Package** is the package where the **Spring Boot Start Class** is located.

Spring Boot performs **Component Scanning** from this package and scans all of its sub-packages.

---

## Example

```
com.example.studentmanagement
│
├── controller
│      └── StudentController
│
├── service
│      └── StudentService
│
├── repository
│      └── StudentRepository
│
└── StudentManagementApplication
```

Since the start class is inside

```
com.example.studentmanagement
```

Spring scans

- controller
- service
- repository

automatically.

---

## Why is it Important?

Suppose your structure is

```
com.example.controller

com.demo.service

com.test.repository

com.main.Application
```

Spring will **not** scan all these packages automatically.

You must specify

```java
@ComponentScan(basePackages = {
    "com.example",
    "com.demo",
    "com.test"
})
```

---

## Best Practice

Always keep the Start Class in the **root package**.

---

## Interview Question

**Why should the Start Class be placed in the root package?**

Because Spring Boot performs Component Scanning from the package containing the Start Class.

---

# 10. What is SpringApplication.run() Method?

## Interview Definition

`SpringApplication.run()` is the method that starts the Spring Boot application.

It creates the IoC Container, performs component scanning, applies auto-configuration, creates beans, and starts the embedded server (if required).

---

## Syntax

```java
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {

        SpringApplication.run(DemoApplication.class, args);

    }
}
```

---

## Internal Working

```text
main()
      ↓
SpringApplication.run()
      ↓
Create SpringApplication Object
      ↓
Create ApplicationContext (IoC Container)
      ↓
Component Scan
      ↓
Create Beans
      ↓
Dependency Injection
      ↓
Auto Configuration
      ↓
Start Embedded Server (Tomcat)
      ↓
Execute Runners
      ↓
Application Ready
```

---

## Responsibilities

- Creates IoC Container
- Reads configuration
- Performs Component Scanning
- Performs Dependency Injection
- Starts Embedded Server
- Executes Runners

---

## Interview Question

**Can a Spring Boot application start without `SpringApplication.run()`?**

No.

Without this method, Spring Boot cannot create the IoC Container or start the application.

---

# 11. How is IoC Container Created in Spring Boot?

## Interview Definition

The IoC Container is created automatically when `SpringApplication.run()` is executed.

---

## Flow

```text
main()
      ↓
SpringApplication.run()
      ↓
Create ApplicationContext
      ↓
IoC Container Ready
```

---

## What Happens Inside?

Spring Boot

- Reads configuration
- Scans packages
- Creates beans
- Injects dependencies
- Manages bean lifecycle

---

## Interview Question

**Do we manually create the IoC Container in Spring Boot?**

No.

Spring Boot creates it automatically.

---

# 12. Which Class is Used to Start IoC in Spring Boot?

## Interview Answer

The class used is

```java
SpringApplication
```

Specifically,

```java
SpringApplication.run()
```

creates and starts the IoC Container.

---

## Example

```java
SpringApplication.run(
    DemoApplication.class,
    args
);
```

---

## Interview Point

`SpringApplication` is one of the core classes in Spring Boot.

---

# 13. What is the Return Type of SpringApplication.run()?

## Interview Definition

The return type is

```java
ConfigurableApplicationContext
```

---

## Example

```java
ConfigurableApplicationContext context =
SpringApplication.run(
DemoApplication.class,
args
);
```

---

## Why Return the Context?

It allows us to

- Get Beans
- Close Context
- Access Environment
- Publish Events

---

## Example

```java
StudentService service =
context.getBean(StudentService.class);
```

---

## Interview Question

**What is the return type of `SpringApplication.run()`?**

`ConfigurableApplicationContext`.

---

# 14. What is Banner in Spring Boot?

## Interview Definition

The Banner is the ASCII art displayed in the console when the Spring Boot application starts.

---

Example

```
  .   ____          _
 /\\ / ___'_ __ _ _(_)_ __
( ( )\___ | '_ | '_| | '_ \
 \\/ ___)| |_)| | | | | || |
  ' |____| .__|_| |_|_| |_|
 =========|_|
```

---

## Can We Customize It?

Yes.

Create a file

```
src/main/resources/banner.txt
```

Example

```
Welcome Suraj

Java Backend Developer

Spring Boot Project
```

Spring Boot automatically displays it.

---

## Disable Banner

application.properties

```properties
spring.main.banner-mode=off
```

---

## Modes

```properties
console
```

```properties
log
```

```properties
off
```

---

## Interview Question

**Can we customize the Spring Boot banner?**

Yes.

Create `banner.txt` inside `resources`.

---

# 15. What is Runner in Spring Boot?

## Interview Definition

A Runner executes code automatically **after the Spring Boot application starts successfully**.

---

## Types

- CommandLineRunner
- ApplicationRunner

---

## Example

```java
@Component
public class MyRunner implements CommandLineRunner {

    @Override
    public void run(String... args) {

        System.out.println("Application Started");

    }
}
```

---

## Execution Flow

```text
Application Starts
      ↓
IoC Container Created
      ↓
Beans Created
      ↓
Dependency Injection
      ↓
Application Ready
      ↓
Runner Executes
```

---

## Real Uses

- Insert default users
- Seed database
- Validate configuration
- Load cache
- Print startup logs

---

## Interview Question

**When does a Runner execute?**

After the application is fully initialized.

---

# 16. What is application.properties?

## Interview Definition

`application.properties` is the default configuration file used to configure a Spring Boot application.

It is located in

```
src/main/resources
```

---

## Common Configurations

### Server Port

```properties
server.port=9090
```

---

### Application Name

```properties
spring.application.name=StudentManagement
```

---

### Database

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/studentdb

spring.datasource.username=root

spring.datasource.password=root
```

---

### Logging

```properties
logging.level.root=INFO
```

---

### Banner

```properties
spring.main.banner-mode=off
```

---

### Context Path

```properties
server.servlet.context-path=/api
```

---

## Why Do We Use It?

Instead of hardcoding values,

we keep configuration separate from code.

This makes the application easy to maintain.

---

## Alternative

Spring Boot also supports

```
application.yml
```

---

## Interview Question

**Where is `application.properties` located?**

```
src/main/resources
```

---

# ⭐ Frequently Asked Interview Questions

### Q1. What is Base Package?

The package containing the Start Class from which Spring begins Component Scanning.

---

### Q2. What does `SpringApplication.run()` do?

It starts the Spring Boot application by creating the IoC Container, performing component scanning, auto-configuration, dependency injection, and starting the embedded server if needed.

---

### Q3. Who creates the IoC Container?

`SpringApplication.run()`.

---

### Q4. Which class starts the IoC Container?

`SpringApplication`.

---

### Q5. What is the return type of `SpringApplication.run()`?

`ConfigurableApplicationContext`.

---

### Q6. What is Banner?

The startup ASCII art displayed when Spring Boot starts.

---

### Q7. Can we customize the Banner?

Yes.

Create `banner.txt` inside `resources`.

---

### Q8. What is a Runner?

A component that executes code automatically after the application has started successfully.

---

### Q9. Types of Runners?

- CommandLineRunner
- ApplicationRunner

---

### Q10. What is `application.properties`?

The default configuration file used to configure Spring Boot applications.

---

# 🚀 One-Minute Revision

- Base Package = Package containing the Start Class.
- `SpringApplication.run()` starts the application.
- IoC Container is created automatically.
- `SpringApplication` starts the IoC Container.
- `SpringApplication.run()` returns `ConfigurableApplicationContext`.
- Banner = Startup ASCII logo.
- Customize Banner using `banner.txt`.
- Runners execute after application startup.
- `application.properties` stores application configuration.
- Keep the Start Class in the root package for proper component scanning.

# Spring Boot Interview Notes - Part 3

> **Interview Level:** Beginner → Intermediate
>
> **Spring Boot Version:** 3.x

---

# 17. Dependency Injection (DI)

## Interview Definition

**Dependency Injection (DI)** is a design pattern in which the Spring IoC Container creates the required objects (dependencies) and injects them into other objects instead of the objects creating them manually.

In simple words:

> "Don't create the object yourself. Let Spring create and provide it."

---

## Without Dependency Injection

```java
public class StudentService {

    StudentRepository repository = new StudentRepository();

}
```

### Problem

- Tight Coupling
- Difficult to Test
- Hard to Maintain

---

## With Dependency Injection

```java
@Service
public class StudentService {

    private final StudentRepository repository;

    public StudentService(StudentRepository repository) {
        this.repository = repository;
    }

}
```

Spring creates the repository object and injects it into the service.

---

## Advantages

- Loose Coupling
- Easy Testing
- Easy Maintenance
- Better Readability
- Reusable Code

---

## Interview Question

### What is Dependency Injection?

Dependency Injection is a design pattern where Spring provides the required dependencies instead of allowing the class to create them itself.

---

# 18. Types of Dependency Injection

Spring supports three types of Dependency Injection.

## 1. Constructor Injection ✅ (Recommended)

```java
@Service
public class StudentService {

    private final StudentRepository repository;

    public StudentService(StudentRepository repository) {
        this.repository = repository;
    }

}
```

### Advantages

- Mandatory dependencies
- Supports immutable objects
- Easy unit testing
- Prevents NullPointerException
- Recommended by Spring Team

---

## 2. Setter Injection

```java
@Service
public class StudentService {

    private StudentRepository repository;

    @Autowired
    public void setRepository(StudentRepository repository) {
        this.repository = repository;
    }

}
```

### Advantages

- Optional dependencies
- Dependency can be changed later

### Disadvantages

- Object may be created without dependencies
- Can cause NullPointerException

---

## 3. Field Injection

```java
@Service
public class StudentService {

    @Autowired
    private StudentRepository repository;

}
```

### Advantages

- Less code

### Disadvantages

- Difficult to test
- Hidden dependency
- Cannot use final
- Not recommended

---

## Interview Answer

### Which Dependency Injection is best?

Constructor Injection.

Because

- Mandatory dependencies
- Better testing
- Immutable objects
- Recommended by Spring

---

# 19. Bean Scope

## Definition

Bean Scope determines **how many objects** Spring creates for a bean.

---

## Types

### Singleton (Default)

One object per Spring Container.

```java
@Component
@Scope("singleton")
```

---

### Prototype

New object every time.

```java
@Component
@Scope("prototype")
```

---

### Request

One object per HTTP request.

```java
@RequestScope
```

---

### Session

One object per HTTP session.

```java
@SessionScope
```

---

### Application

One object for the entire ServletContext.

```java
@ApplicationScope
```

---

## Interview Question

### Default Bean Scope?

Singleton.

---

# 20. Autowiring

## Definition

Autowiring is the process by which Spring automatically injects dependencies.

---

## Example

```java
@Service
public class StudentService {

    private final StudentRepository repository;

    public StudentService(StudentRepository repository) {
        this.repository = repository;
    }

}
```

Spring automatically injects the repository bean.

---

## Advantages

- No manual object creation
- Less code
- Loose Coupling
- Better Maintainability

---

## Interview Question

### What is Autowiring?

Automatic injection of dependencies by Spring.

---

# 21. Autowiring Modes

Although modern Spring Boot primarily uses annotation-based injection, traditional Spring supports these modes.

---

## byName

Bean is injected using its name.

---

## byType

Bean is injected using its type.

---

## constructor

Bean is injected through constructor.

---

## no

No autowiring.

---

## annotation

Uses annotations such as

```java
@Autowired
```

---

## Interview Point

Modern Spring Boot mainly uses

- Constructor Injection
- @Autowired
- @Qualifier
- @Primary

instead of XML autowiring modes.

---

# 22. Bean Lifecycle

## Definition

Bean Lifecycle describes what happens from bean creation until bean destruction.

---

## Lifecycle Steps

```text
Container Starts
      ↓
Bean Created
      ↓
Dependency Injection
      ↓
@PostConstruct
      ↓
Bean Ready
      ↓
Application Running
      ↓
@PreDestroy
      ↓
Bean Destroyed
```

---

## Initialization

```java
@PostConstruct
public void init(){

}
```

Runs after dependency injection.

---

## Destruction

```java
@PreDestroy
public void destroy(){

}
```

Runs before bean destruction.

---

## Interview Question

### Which annotations are used in Bean Lifecycle?

- @PostConstruct
- @PreDestroy

---

# 23. How to Represent a Java Class as a Spring Bean?

A Java class becomes a Spring Bean when Spring manages it.

---

## Method 1 (Most Common)

```java
@Component
```

---

## Method 2

```java
@Service
```

---

## Method 3

```java
@Repository
```

---

## Method 4

```java
@Controller
```

---

## Method 5

```java
@RestController
```

---

## Method 6

Using

```java
@Bean
```

inside

```java
@Configuration
```

Example

```java
@Configuration
public class AppConfig {

    @Bean
    public Student student() {

        return new Student();

    }

}
```

---

## Interview Question

### How do you make a Java class a Spring Bean?

Using

- @Component
- @Service
- @Repository
- @Controller
- @RestController
- @Bean

---

# 24. @Component vs @Bean

## @Component

### Definition

Used on the class itself.

Spring automatically discovers it using Component Scanning.

---

### Example

```java
@Component
public class StudentService {

}
```

---

## @Bean

### Definition

Used on a method inside a configuration class.

---

### Example

```java
@Configuration
public class AppConfig {

    @Bean
    public Student student() {

        return new Student();

    }

}
```

---

## Difference

| @Component | @Bean |
|------------|-------|
| Applied on Class | Applied on Method |
| Automatically discovered | Manually declared |
| Requires Component Scan | Inside @Configuration |
| Used for own classes | Often used for third-party classes or custom bean creation |

---

## When to Use?

Use **@Component** when you own the source code of the class.

Use **@Bean** when:
- You want custom bean creation logic.
- You are creating beans for third-party classes that you cannot annotate.

---

# ⭐ Frequently Asked Interview Questions

### Q1. What is Dependency Injection?

Spring provides dependencies instead of allowing objects to create them.

---

### Q2. Which Dependency Injection is best?

Constructor Injection.

---

### Q3. Why is Constructor Injection recommended?

- Mandatory dependencies
- Easy testing
- Immutable objects
- Better design
- Recommended by Spring

---

### Q4. Default Bean Scope?

Singleton.

---

### Q5. What is Autowiring?

Automatic dependency injection performed by Spring.

---

### Q6. Which annotations define Bean Lifecycle?

- @PostConstruct
- @PreDestroy

---

### Q7. How do you create a Spring Bean?

Using

- @Component
- @Service
- @Repository
- @Controller
- @RestController
- @Bean

---

### Q8. Difference between @Component and @Bean?

- @Component is placed on a class and is discovered automatically through component scanning.
- @Bean is placed on a method inside a `@Configuration` class and explicitly returns the object that should become a bean.

---

# 💡 MNC Interview Tips

### Prefer Constructor Injection

Modern Spring Boot applications should use constructor injection instead of field injection because it:
- Makes dependencies mandatory.
- Supports `final` fields.
- Simplifies unit testing.
- Avoids partially initialized objects.

---

### Understand Bean Scope

Remember:
- **Singleton** → One bean per Spring container (default).
- **Prototype** → New bean every time it is requested.
- **Request** → One bean per HTTP request.
- **Session** → One bean per HTTP session.
- **Application** → One bean for the entire web application.

---

### @Component vs @Bean

A common interview question is:

> "When would you use `@Bean` instead of `@Component`?"

Answer:

> Use `@Component` for your own classes that Spring can discover through component scanning. Use `@Bean` when creating beans for third-party classes or when you need custom object creation logic.

---

# 🚀 One-Minute Revision

- Dependency Injection = Spring provides dependencies.
- Constructor Injection = ✅ Best Practice.
- Setter Injection = Optional dependencies.
- Field Injection = Avoid in production.
- Default Bean Scope = Singleton.
- Autowiring = Automatic dependency injection.
- Bean Lifecycle = Create → Inject → `@PostConstruct` → Ready → `@PreDestroy` → Destroy.
- Spring Beans can be created using `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController`, or `@Bean`.
- `@Component` is discovered automatically; `@Bean` is declared manually inside a `@Configuration` class.