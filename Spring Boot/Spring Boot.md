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
## Exit Code 0

If only `spring-boot-starter` is present:
- IoC Container starts.
- Beans are created.
- No web server starts.
- Application exits successfully with Exit Code 0.

## Interview Questions

### What is @SpringBootApplication?
A convenience annotation combining @SpringBootConfiguration, @EnableAutoConfiguration and @ComponentScan.

### What does SpringApplication.run() do?
Starts the Spring Boot application, creates the IoC container, performs component scanning, dependency injection, auto configuration and starts the embedded server if required.

### Best Practices
- Keep the main class in the root package.
- Use @SpringBootApplication only once.
- Exit Code 0 means successful execution.

## Quick Revision

- Main Class = Entry Point
- @SpringBootApplication = 3 annotations combined
- SpringApplication.run() starts Spring Boot
- Main class should be in the root package
- Exit Code 0 = Success


### NOTE - SpringApplication is a predefined class and it will identify what type of application we have created based on dependencies added in pom.xml file.

        1) standalone application when (spring-boot-started)
            Class Name : "AnnotationConfigAppliationContext"[spring-boot used this class to start the IOC container]
        2) Web application when (spring-boot-starter-web)
            Class Name : "AnnotationConfigServletWebServerAppliationContext"
            [spring-boot used this class to start the IOC container]
        3) Reactive application when (spring-boot-starter-webflux)
           Class Name : "AnnotationConfigReactivetWebServerAppliationContext"
            [spring-boot used this class to start the IOC container]

- Based on type of application , It will start IOC container.   
- If we add all 3 starter the Web application starter will have the highest priority    
- run() method will print banner on the console(i.e --> Spring-logo) 
- run() method will start IOC container
- run() method will call runners
### runner is used to run any code only one time when the boot application started
- run() method will return the reference/context of IOC container  
- return type of run() method is ConfigurableApplicationContext

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

## Q) What is Banner in Spring Boot?
- When we run boot application, it will print spring logo on the console that is called as Banner
- Spring boot banner has 3 modes

        1) Off
        2) Log
        3) Console(default)

- We can set banner mode using below property  

        spring.main.banner-mode = off [to turn it off]

- we can customize the banner txt in Spring boot application by creating "banner.txt" file in src/main/resource folder  

## Runners in Spring boot
- When you click Run, the following happens:

        JVM Starts
            ↓
        Spring Boot Starts
            ↓
        IoC Container Created
            ↓
        Beans Created
            ↓
        Dependency Injection
            ↓
        Application Ready

- runners are used to execute the logic only once when application got started
- SpringApplication.run() method will call runners
- in Spring boot we have 2 types

        1) ApplicationRunner()
        2) CommandLineRunner()

- We have to implement ApplicationRunner or CommandLineRunner Interface and whenever we implement an interface we have to @Override all the methods in it   

## What are Runners?

Runners are special interfaces provided by Spring Boot that allow you to execute code **immediately after the Spring Boot application has started successfully**.

They are mainly used for startup tasks such as:
- Loading initial data into the database
- Checking database connectivity
- Initializing cache
- Reading configuration files
- Printing startup information
- Calling external APIs during startup

## CommandLineRunner

`CommandLineRunner` is a Spring Boot interface whose `run()` method executes automatically after the application starts.

### Syntax

```java
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

@Component
public class MyRunner implements CommandLineRunner {

    @Override
    public void run(String... args) throws Exception {
        System.out.println("Application Started Successfully");
    }
}
```

## Explanation

### `@Component`

Registers this class as a Spring Bean.

### `implements CommandLineRunner`

Tells Spring Boot that this class should execute after startup.

### `run(String... args)`

This method is automatically called once the application is ready.

The parameter

```java
String... args
```

contains all command-line arguments.

Example

```bash
java -jar app.jar Suraj Java Spring
```

Then

```java
args[0] = "Suraj"
args[1] = "Java"
args[2] = "Spring"
```

## Advantages

- Very easy to use
- Suitable for simple startup logic
- Good for beginners

## Real Project Uses
- Loading data from DB to cache memory
- Insert default admin user
- Load sample data
- Print startup logs
- Check database connection

## ApplicationRunner

`ApplicationRunner` is another Spring Boot interface that executes after startup.

Instead of receiving raw strings, it receives an `ApplicationArguments` object.

### Syntax

```java
import org.springframework.boot.ApplicationArguments;
import org.springframework.boot.ApplicationRunner;
import org.springframework.stereotype.Component;

@Component
public class MyRunner implements ApplicationRunner {

    @Override
    public void run(ApplicationArguments args) throws Exception {

        System.out.println("Application Started Successfully");

    }
}
```

## What is ApplicationArguments?

Spring wraps the command-line arguments into an object.

This object provides useful methods like:

```java
args.containsOption("name");
args.getOptionValues("name");
args.getNonOptionArgs();
```

Example

Run application as:

```bash
java -jar app.jar --name=Suraj --city=Delhi Java
```

Now,

```java
args.containsOption("name");
```

returns

```text
true
```

and

```java
args.getOptionValues("name");
```

returns

```text
[Suraj]
```

## Difference Between CommandLineRunner and ApplicationRunner

| Feature | CommandLineRunner | ApplicationRunner |
|----------|-------------------|-------------------|
| Interface | CommandLineRunner | ApplicationRunner |
| Method | `run(String... args)` | `run(ApplicationArguments args)` |
| Arguments | Raw String Array | Parsed Arguments Object |
| Complexity | Simple | More Flexible |
| Best For | Simple startup tasks | Complex command-line argument handling |

## Which One Should You Use?

### Use CommandLineRunner when:

- Startup task is simple
- No advanced command-line argument parsing is needed
- You just want to execute startup logic


### Use ApplicationRunner when:

- You need command-line options
- You want parsed arguments
- Your application has multiple startup parameters


## Multiple Runners

If multiple runners exist,

Spring can execute them in a specific order using `@Order`.

Example

```java
@Component
@Order(1)
public class FirstRunner implements CommandLineRunner {

    @Override
    public void run(String... args) {

        System.out.println("First Runner");

    }
}
```

```java
@Component
@Order(2)
public class SecondRunner implements CommandLineRunner {

    @Override
    public void run(String... args) {

        System.out.println("Second Runner");

    }
}
```

Output

```text
First Runner
Second Runner
```

## Internal Working

```text
Run Application
      ↓
SpringApplication.run()
      ↓
ApplicationContext Created
      ↓
Beans Created
      ↓
Dependency Injection
      ↓
Auto Configuration
      ↓
Application Ready
      ↓
Runner Executes
```

---

## Real-Life Example

Suppose you are building an E-Commerce application.

Whenever the application starts, you want to

- Create Admin User
- Insert Default Categories
- Load Products
- Verify Database Connection

Instead of writing this inside `main()`, you use a Runner.

## Advantages of Runners

- Automatic execution after startup
- Keeps startup logic separate
- Easy initialization
- Useful in real-world applications


## Q1. What is CommandLineRunner?

A Spring Boot interface that executes the `run(String... args)` method automatically after the application starts.

## Q2. What is ApplicationRunner?

A Spring Boot interface that executes the `run(ApplicationArguments args)` method after startup and provides structured access to command-line arguments.

## Q3. What is the difference?

**CommandLineRunner**
- Receives raw String arguments

**ApplicationRunner**
- Receives parsed `ApplicationArguments`

## Q4. When do Runners execute?

After

- IoC Container is created
- Bean creation
- Dependency Injection
- Auto Configuration
- Application Startup

## Q5. Can we have multiple runners?

Yes.

Use

```java
@Order(1)
```

to specify execution order.

## Best Practices

- Keep runner logic small.
- Do not write heavy business logic inside runners.
- Use runners only for startup initialization.
- Use `@Order` when multiple runners are present.
- Prefer `ApplicationRunner` when working with command-line options.

## One-Minute Revision

✅ Runner = Executes after Spring Boot starts.

✅ Types:
- CommandLineRunner
- ApplicationRunner

✅ CommandLineRunner

- `run(String... args)`
- Raw String arguments

✅ ApplicationRunner

- `run(ApplicationArguments args)`
- Parsed command-line arguments

✅ `@Order` controls execution order.

✅ Common Uses

- Database initialization
- Cache loading
- Startup validation
- Logging
- Reading configuration

## Interview Cheat Sheet

| Question | Answer |
|----------|--------|
| What is a Runner? | Executes code after Spring Boot startup |
| Types of Runners? | CommandLineRunner and ApplicationRunner |
| Which receives String arguments? | CommandLineRunner |
| Which receives ApplicationArguments? | ApplicationRunner |
| Which is more flexible? | ApplicationRunner |
| Annotation for execution order? | `@Order` |
| When do runners execute? | After the application is fully initialized |
| Common Uses? | Data loading, cache initialization, startup tasks |


## Easy Trick to Remember

**CommandLineRunner**

> "Give me the arguments exactly as they were typed."

**ApplicationRunner**

> "Give me the arguments in an organized and easy-to-use format."

**Summary**

- Both are startup hooks in Spring Boot.
- Both execute after the application is fully initialized.
- `CommandLineRunner` is simple and uses `String... args`.
- `ApplicationRunner` is more powerful and uses `ApplicationArguments`.
- Use runners for startup initialization tasks, not for long-running business logic.     

### NOTE - If anyone forgets to write @Autowired while performing Setter Injection there is a chance of getting Nullpointerexception and in Field Injection, it breaks the oops concept bcz it Implements SI using reflection API but in constructor Injection there is no such problem even if we dnt give @Autowired the obj will still be created if there is single constructor and if there are multiple constructor the by defauly the 0-param constructor's object will be created if we have to create some specific constructors obj then we'll have to give @Autowired to that

### NOTE - there is no use for @Autowired on Primitive data type , we should only use it for reference data type

# Difference Between @Component, @Service, and @Repository

## First, What is a Stereotype Annotation?

A **Stereotype Annotation** tells Spring:

> "This class should be managed by the Spring IoC Container."

When Spring performs **Component Scanning**, it looks for these annotations and creates beans automatically.

The most common stereotype annotations are:

- `@Component`
- `@Service`
- `@Repository`
- `@Controller`
- `@RestController`

---

# 1. @Component

## Definition

`@Component` is the **generic stereotype annotation**.

It is used for any Java class that should become a Spring Bean but doesn't belong to a specific layer.

---

## Example

```java
@Component
public class EmailUtil {

    public void sendMail() {
        System.out.println("Sending Email...");
    }

}
```

Spring creates an object of this class automatically.

---

## When to Use?

Use `@Component` for:

- Utility Classes
- Helper Classes
- Validator Classes
- Common Services
- Any class that doesn't fit into Service, Repository, or Controller

---

# 2. @Service

## Definition

`@Service` is a specialization of `@Component`.

It represents the **Business Logic Layer**.

---

## Example

```java
@Service
public class StudentService {

    public void saveStudent() {

        System.out.println("Business Logic");

    }

}
```

---

## Responsibilities

- Business Logic
- Calculations
- Validation
- Calling Repository
- Calling External APIs

---

## Why Use @Service Instead of @Component?

Both create beans.

But `@Service` clearly tells another developer:

> "This class contains business logic."

This improves readability and maintainability.

---

# 3. @Repository

## Definition

`@Repository` is also a specialization of `@Component`.

It represents the **Data Access Layer (DAO Layer).**

---

## Example

```java
@Repository
public class StudentRepository {

    public void save() {

        System.out.println("Saving Student");

    }

}
```

---

## Responsibilities

- Database Operations
- CRUD Operations
- SQL Queries
- JPA Operations
- Data Access

---

## Special Feature of @Repository

Unlike `@Component` and `@Service`,

`@Repository` provides **Exception Translation**.

Example

If JDBC throws

```text
SQLException
```

Spring converts it into

```text
DataAccessException
```

This makes exception handling easier and independent of the database technology.

---

# Internal Working

```text
@Component
       │
       ▼
Spring Creates Bean

@Service
       │
       ▼
Spring Creates Bean

@Repository
       │
       ▼
Spring Creates Bean
```

All three annotations create Spring Beans.

The difference is mainly **their intended role**.

---

# Relationship

```text
@Component
      ▲
      │
 ┌────┴────┐
 │         │
@Service  @Repository
```

Both `@Service` and `@Repository` are specialized forms of `@Component`.

---

# Layered Architecture

```text
Client
   │
   ▼
@Controller / @RestController
   │
   ▼
@Service
   │
   ▼
@Repository
   │
   ▼
Database
```

---

# Comparison Table

| Feature | @Component | @Service | @Repository |
|----------|------------|-----------|--------------|
| Bean Creation | ✅ Yes | ✅ Yes | ✅ Yes |
| Component Scanning | ✅ Yes | ✅ Yes | ✅ Yes |
| Layer | Generic | Business Layer | Data Access Layer |
| Business Logic | ❌ No | ✅ Yes | ❌ No |
| Database Logic | ❌ No | ❌ No | ✅ Yes |
| Exception Translation | ❌ No | ❌ No | ✅ Yes |
| Recommended Use | Utility/Helper Classes | Service Layer | Repository/DAO Layer |

---

# Real Project Example

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
├── util
│      └── EmailUtil
```

### StudentController

```java
@RestController
public class StudentController {

}
```

Handles HTTP requests.

---

### StudentService

```java
@Service
public class StudentService {

}
```

Contains business logic.

---

### StudentRepository

```java
@Repository
public class StudentRepository {

}
```

Interacts with the database.

---

### EmailUtil

```java
@Component
public class EmailUtil {

}
```

Provides utility methods.

---

# Frequently Asked Interview Questions

## Q1. What is the difference between @Component and @Service?

Technically, both create Spring Beans.

The difference is their purpose.

- `@Component` → Generic bean.
- `@Service` → Business logic layer.

---

## Q2. What is the difference between @Service and @Repository?

- `@Service` contains business logic.
- `@Repository` handles database operations and supports exception translation.

---

## Q3. Does Spring create beans for all three?

Yes.

All three annotations register the class as a Spring Bean during component scanning.

---

## Q4. Which annotation provides Exception Translation?

`@Repository`

It converts database-specific exceptions into Spring's `DataAccessException`.

---

## Q5. Can I use @Component instead of @Service?

Yes, technically it will work because `@Service` is a specialization of `@Component`.

However, it is **not recommended** because `@Service` makes the code more readable and clearly indicates that the class contains business logic.

---

# Best Practices

- Use `@Component` for generic helper or utility classes.
- Use `@Service` for business logic classes.
- Use `@Repository` for data access classes.
- Follow the layered architecture for clean, maintainable code.

---

# One-Minute Revision

- `@Component` = Generic Spring Bean.
- `@Service` = Business Logic Layer.
- `@Repository` = Database Layer.
- All three are discovered by **Component Scanning**.
- All three create Spring Beans.
- `@Repository` provides **Exception Translation**.
- `@Service` and `@Repository` are specialized forms of `@Component`.

---

# Easy Trick to Remember

🏠 **Think of an Online Shopping Application**

- 🛠 **@Component** → Helper (Email Utility, PDF Generator, File Utility)
- 🧠 **@Service** → Manager who decides the business rules (discounts, order validation, payment flow)
- 🗄 **@Repository** → Clerk who stores and retrieves data from the database


