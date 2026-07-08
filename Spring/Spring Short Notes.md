
# Spring Core - Short Notes

## 1. What is Spring Bean?

### Definition
A Spring Bean is a Java object that is created, managed and destroyed by the Spring IoC Container.

### Key Points
- Normal Java Object (POJO)
- Managed by Spring
- Lifecycle controlled by IoC Container
- Used for Dependency Injection

### Bean Creation
- `@Component`
- `@Service`
- `@Repository`
- `@Controller`
- `@RestController`
- `@Bean`

### Interview Points
- Bean = Object managed by Spring.
- Every Bean is a Java object, but every Java object is **not** a Spring Bean.

---

## 2. How to Represent a Java Class as Spring Bean?

### Annotation-Based

```java
@Component
public class StudentService {
}
```

### Java Configuration

```java
@Configuration
public class AppConfig {

    @Bean
    public StudentService studentService() {
        return new StudentService();
    }
}
```

### XML Configuration

```xml
<bean id="studentService"
      class="com.example.StudentService"/>
```

### Interview Points
- Spring scans classes using Component Scanning.
- Bean names must be unique.

---

## 3. What is IoC Container?

### Definition
IoC (Inversion of Control) Container creates, stores, manages and injects Spring Beans.

### Responsibilities
- Create Beans
- Store Beans
- Inject Dependencies
- Manage Bean Lifecycle

### Types
- BeanFactory
- ApplicationContext

### Interview Points
- IoC transfers object creation from programmer to Spring.
- Dependency Injection is provided by the IoC Container.

---

## 4. What is Bean Configuration File?

### Definition
Configuration file tells Spring:
- Which Beans to create
- Bean dependencies
- Bean properties

### Types
- XML (`beans.xml`)
- Java Configuration (`@Configuration`)
- Annotation-based (Spring Boot - Most Common)

### Interview Points
- XML is used in older Spring projects.
- Spring Boot mainly uses annotations.

---

## 5. How to Start IoC Container?

### XML-Based

```java
ApplicationContext context =
new ClassPathXmlApplicationContext("beans.xml");
```

### Spring Boot

```java
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

### Interview Points
- `SpringApplication.run()` starts the IoC Container.
- Beans are created and registered in the container.

---

## 6. First Application Development Using Spring Core

### Steps

1. Create POJO Class
2. Configure Bean
3. Start IoC Container
4. Retrieve Bean
5. Call Business Method

### Flow

Application Starts
→ IoC Container Starts
→ Bean Created
→ Dependency Injection
→ Bean Ready
→ Business Logic Executes

### Interview Points
- Never create managed objects using `new`.
- Retrieve Spring Beans using `getBean()`.

---

# Frequently Asked Interview Questions

1. What is a Spring Bean?
2. What is IoC?
3. Difference between Java Object and Spring Bean?
4. What is IoC Container?
5. Types of IoC Containers?
6. How do you create a Bean?
7. What is Bean Configuration?
8. How does Spring Boot start the IoC Container?
9. What is `SpringApplication.run()`?
10. What is the role of `ApplicationContext`?

---

# One-Minute Revision

- Spring Bean = Object managed by Spring.
- IoC Container = Creates and manages Beans.
- BeanFactory = Basic Container.
- ApplicationContext = Advanced Container.
- Configuration = XML / Java / Annotation.
- `SpringApplication.run()` starts Spring Boot.
- Bean retrieved using `getBean()`.

## 7. Dependency Injection (DI)
- Spring creates and injects objects.
- Types: Setter Injection (<property>), Constructor Injection (<constructor-arg>), Field Injection (@Autowired).
- Constructor Injection is preferred.

## 8. BeanFactory vs ApplicationContext
- BeanFactory: Basic, Lazy Loading.
- ApplicationContext: Advanced, Eager Loading, supports Events, AOP, i18n.
- Spring Boot uses ApplicationContext.

## 9. Lazy Loading vs Eager Loading
- Lazy: Bean created when requested.
- Eager: Bean created at container startup.

## 10. Bean Scopes
- Singleton (default): One bean per container.
- Prototype: New bean every request.

## 11. Autowiring & Modes
- @Autowired performs automatic dependency injection.
- XML modes: no, byName, byType, constructor.
- @Qualifier chooses a specific bean.
- @Primary marks default bean.

## 12. Bean Life Cycle
1. Container Starts
2. Bean Created
3. Dependency Injection
4. Initialization (@PostConstruct)
5. Bean Ready
6. Bean Used
7. Destruction (@PreDestroy)

## Interview Points
- DI reduces tight coupling.
- Constructor Injection is recommended.
- BeanFactory = Lazy.
- ApplicationContext = Eager.
- Default scope = Singleton.
- Prototype beans are not fully managed during destruction.
