# Programming lang vs Technology vs Framework

## Q) What is a programming language ?

        a) programming lang contains set of instructions 
        ex: C, C++, Java, C#
        b) Every programming language will follow set of syntaxes
        c) using programming language We can develop 
                applications/toos/software/technologies/Framework
        d) we can develop only stand alone applications                 


## Q) What is Technology?

        a) Technology is a software which is developed by using programming language
                ex: srvlets, JSP, JDBC
        b) Technologies are used to resolve common problems/ address common requirements/to simplify our tasks
        c) By using technologies we can develop our applications    


## Q) What is Framework?

        a) Framework is a semi developed software
        b) It provides common logics required for application development
                ex:
                        1) Capture form data
                        2) Validate form data
                        3) Create connection pool
                        4) DB CRUD etc.....

        c) It provides re-usable components
        d) For ex, every Java Developer should write below lines of code to perform DB operation

                Class.forName("");
                DM.getConn("");
                createStatement()
                executeQuerry()
                process ResultSet()
                close connection


### NOTE - If we are writing same code for multiple times then it is called a boiler plate code / redundant code.


        e) To avoid duplicate code/ common logic implementation, Frameworks came into picture.

                Project = Business Logics + Common Logics

        f) Frameworks provides common logics required for the projects so that we only have to focus on only business Logic development
        g) It will improve developers productivity, can do more work in less time

                ex: 
                JAVA=> Hibernate, Spring, Struts, Spring Boot
                .Net=> WCF
                Python=>  DJango, Flask
                Salesforce=> Lightning etc......


### NOTE - Frameworks will be developed by using Programming Language only.

## Tools :

        a) Tools are used to automate manual work
        
                Ex: 
                        1) Maven
                        2) JIRA
                        3) JENKINS
                        4) JMETER
                        5) POSTMAN
                        6) SONARQUBE etc....
                
---
# Application Architecture


Project = Frontend + Backend + Database

Frontend : Presentation Logic / User Interface Logic

        Frontend Techstack:
                1) HTML & CSS
                2) Java Script
                3) Bootstrap
                4) Angular (or) React JS (or) Vue JS

Backend : Web Layer(REST APIs) + Business Layer + Intergation layer + DAO layer

        Backend Techstack:
                1) Java & J2EE
                2) Spring Core
                3) Spring boot
                4) JPA
                5) REST APIs
                6) JSON
                7) Microservices
                8) Security
                9) Kafka + Redis
                10) Reactive programming

Database : Persistant Store
        ex: Oracle, MySQL, Postgres, Mongo DB etc....

Tools : Maven + Git Hub + Log4J + JUnit + Jenkins + SonarQube + JIRA + Docker + Kubernetes  

Cloud Platforms : AWS / Azure / GCP

# Architecture Types 
## 1) Monolith Architecture 
        a) developing all requirements as one application
        b) outdated, bcz maintenance will be difficult
        c) even for small changes baar baar poora project deploy krna pdega
        d) ek functionality me change krenge to baaki functons pr bhi effect hoga
## 2) Microservices Architecure
        a) divide and conquer
        b) divide the project into diff-diff parts 
        c) maintenance will be very easy
        d) loosely coupled APIs
        e) easy deployment 
        f) no single point of failure

## Types of frameworks 
### 1) Frontend Framework : 
                to develop user interface in the project
                ex: Angular
### 2) Web Frameworks :
                to develop web layer in the project 
                ex: Struts(Outdated)
### 3) ORM Frameworks : 
                to develop persistance layer in the project 
                ex: Hibernate 

## Struts Framework Disadvantages :                

                a) By using Struts we can develop only Web Layer in the project (Controllers)
                b) By using hibernate we can develop only Data Access Layer (Persistence Layer)

## Notes : To overcome the problems of Struts framework, Spring Framework came into market.

## Spring Framework :

                a) Spring Framework is called as Application Development Framework
                b) By using Spring Framework we can develop end to end application
                c) Spring is free & open source framework
                d) Spring framework is developed in Modular fashion
                e) Spring framework means collection of modules

## Spring Modules :

                1) Spring core
                2) Spring context
                3) Spring JDBC
                4) Spring ORM
                5) Spring AOP
                6) Spring Web MVC
                7) Spring security
                8) Spring social
                9) Spring Batch
                10) Spring Data JPA
                11) Spring REST
                12) Spring Cloud

### NOTE : Spring is a very flexible framework. It will not force to use all modules. We can choose based on our requirements.

                a) Spring is a versatile framework(Easily it can be integrated with other frameworks)
                b) The current version of Spring Framework 7.0
                c) Spring framework is under license of VM ware

## 1) Spring core : It is base module in the spring framework
=> Spring core module providing fundamental concepts of spring framework 

                1) IOC container(Inversion of Control)
                2) Dependency Injection
                3) Bean life cycle
                4) Bean Scopes
                5) Autowiring...   

## 2) Spring Context : It will deal with configurations reequired for our spring application

## 3) Spring AOP : Aspect Oriented Programming 
=> AOP is used to seperate business logic & secondary logics in the project     

                ex: Security, Logging, Tc, Auditing, Exception handling...

### NOTE : If we combine business logic and secondary logic together then we'll face maintenance issues  

## 4) Spring JDBC : Spring JDBC is used to simplify Database communication logic
=> Using Spring JDBC we can directly execute the querry, we dont have to write all the other connections like we do in java JDBC

## 5) Spring Web MVC : It is used to develop both Web application & Distribuited Application

                => Web Application (Customer to Business)
                        ex: Gmail.com, Facebook.com etc
                => Distribuited Applications (Business to Business) / Web Services (or) RESTful Services
                        ex: IRCTC, MakeMyTrip   

## 6) Spring ORM(Object Relation Manager)
=> Spring Framework Having Integration with ORM Frameworks
                ex: Spring ORM, Spring Data JPA etccc..

### NOTE : JDBC will represent data in text format whereas Hibernate ORM will represent data in objects format.

## 7) Spring Security : 

                a) Security is very cruicial for every application
                b) USing spring security We can implement Authentication & Authorization
                c) Spring security with OAuth2.0
                d) Spring Security with JWT (JSON Web Tokens)

## 8) Spring Batch : Batch means bulk operation 

                a) Reading data from excel file and store it into database table
                b) Sending Monthly Statements to customers in email
                c) Sending reminder to customers as Bulk SMS

## 9) Spring cloud : It Provides some common tools to quickly build distribuited systems.    

                a) Provides service register to register microservices
                b) Provides Load balancer to balance the load of our application
                c) Provides Monitoring Facility
                d) PRovides API gateway to have single entry point for all our APIs
                e) Provides Circuit Breaker(Fault tolerant Systems)
                f) Distribuited Messaging 
                g) Routing

## 10) Spring Test : It provides Unit Test framework  

# Spring core

                a) Spring core module is all about managing dependencies among the classes with loosely coupling
                b) In project we will develop several classes. All those classes we can categorize into 3 types -
                        1) POJO
                        2) Java Bean
                        3) Component

## Q) What is POJO? (Plain Old Java Object)
=> Any Java class which can be compiled by using only JDK software is called a POJO class   

                ex1: Below class is a valid pojo
                class Demo{
                        int id;
                        String name;
                }

                ex2:
                class Demo2 extends Thread{
                        int id;
                        String name;
                }

                ex3:
                class Demo3 implememts Runnable{
                        // run method 
                } 
                ex4: not POJO
                class Demon4 implememnts Servlet{ (//part of JEE)
                        //run method
                }

## Q) What is Java Bean ?
 => Any Java class which follows bean specification rules is called as Java beans.

                1) CLass should implememnt serializable interface
                2) Class should have private data members(variables)
                3) Every private should have public getter and setter method
                4) Class should have zero-param constructor

### NOTE : Bean classes are used to write business logic and to store and retrieve data.

## Q) What is component?
=> The java class which contains business logic is called as component class.

                ex: Controllers, Service, DAO classes
                => Controller classes will have logic to deal with Request & Response
                => Service class will have business logic 
                        ex: Generate OTP ,Send OTP, Send Email, Encrypt & DEcrypt Passwords etc
                => DAO Clasees will contain the logic to communicate with database  

---
=> In a project we will develop multiple classes and those classes will be dependent on other classes.

        ex: 
                a) Controller class will call service class methods
                b) Service class will call DAO class methods

=> In java one class can talk to another class in two ways

                1) Inheritance (IS-A) [when we extend the class to use a method]  
                        [not recommended bcz we cant extend another classes as in inheritance the classes are tightly coupled and if we change a method in one class it might effect the another thats why they are tightly coupled]      
                2) Composition (HAS-A) [when we create the object for using the method] 
                        [not recommended bcz if they change the constructor of the engine class it will fail during compilation] 
                        
                        like before it was Engine() and we changed the constructors to Engine(break, fuel)

                        so if we have created 
                        Engine eng = new Engine();
                        (it'll fail)

                        
### Always we need to develop our classes with loosely coupling
- loosely coupling means without creating object and without inheriting properties we should be able to access one class methods in another class.
- If we make any changes in engine class then Car class should not be effected then we can say our classes are loosely coupled.

### To develop classes with loosely coupling we need to use INTERFACE

#### -> Note - A NullPointerException is a runtime exception that occurs when a program attempts to access or invoke a method, field, or operation on an object reference that is null. It is one of the most common exceptions in Java.

        ex: 
        public class Car{
                private IEngine eng; //IEngine is a interface and we are taking it as reference variable

                public Car(IEngine eng){ //created constructor so that who ever wants can initialise their own type of engine.
                        this.eng = eng;
                }

                public void drive(){ // in order to use the drive method it is the the instance method and to use the instance we have to create the object of car
                        int start = eng.start(); //null pointer exception so we'have created a constructor

                        if(start>= 1){
                                sout("journey started..");
                        }else{
                                sout("engine in trouble");
                        }
                }
        }

## Q) What is Dependency Injection?
- The process of injecting one class object into another class is call as "Dependency Injection"
- Dependency Injection is a design pattern where the objects that a class needs (dependencies) are provided from outside instead of the class creating them itself.
In Spring, the **Spring Container** creates and injects these dependencies automatically.
- We can perform DI in 3 ways -

        1) Setter Injection - write the setter method for the variable(private IEngine eng;)
        - Setter injection means , Injecting dependent object in target object using the class setter method

                //Setter
                public void setEng(IEngine eng){
                        this.eng = eng;
                }

                // how to call in main class
                Car car = new Car() //using the zero-param constructor to make the object of the class bcz we cannot perform the setter injection without creating the object of the car class
                car.setEng(new PetrolEngine());

        2) Constructor Injection - write the constructor for the class and give the object on which our class is dependent inside the parameter
        - Injecting dependent object into target object using target class constructor

                //Constructor
                public Car(IEngine eng){
                        this.eng = eng;
                } 

                //how to call in main class
                Car car = new Car(new DieselEngine());

### NOTE - If we use both setter and constructor injection together so first the CI will initialize the value and then the SI will again initialize it therefore "the setter Injection will @Override the constructor Injection"

        3) Field Injection - Injecting dependent object into target class using target class variable is call as Field Injection
        - To perform Field Injection we are using Reflection API 

                public class Car{
                        private IEngine eng; //we can only use private methods inside the class and not outside of it

                        public void drive(){
                                //code
                        }
                }


                NOTE - WE CAN ACCESS PRIVATE VARIABLE OUTSIDE OF CLASS USING REFLECTION API LIKE BELOW

                //in main class
                publiv class Main{
                        public static void main(String[] args) throws exception{
                                Class<?> clz = Class.forName("packqage.Car") //loading the class

                                Field engField = clz.getDeclaredField("eng"); //load the field whose name is "eng"(field object)
                                engField.setAccessible(true);(can be used even outside the class now)

                                Object object = clz.newInstance(); //whatever the class we have loaded we are creating the object for that class

                                Car carObje = (Car) object; //whatever obj we have created using neInstance() method we are type-casting that into Car class object

                                engField.set(carObj, new DieselEngine()); //Injecting value to variable

                                carObje.drive()
                        }
                }

## Q) IOC Container 
- Inversion of control
- IOC is responsible for Dependency Injection in Spring Application
- Dependency Injection means creating and injecting dependent bean objects into target bean classes.
- We need to provide "Java classes + Beans Confirguration" as input for IOC then IOC will perform DI and provides spring beans which are ready to use
### NOTE - IOC Container will manage life cycle of Spring Beans

## Q) What is Spring Bean?
- Any java class whose life cycle(creation to destruction) is managed by IOC Container is called as Spring Bean.
- We can represent Java Class as Spring Bean in 2 ways

        1) XML Approach (Outdated) (Springboot doesn't support XML approach but spring supports both)
                ex: <bean id = "id1" class = "pkg.ClassName" />
        2) Annotation Approch (Recommended)
                ex: @Component, @Service, @Repository etc...

## Q) How to start IOC in spring?
1) BeanFactory (outdated)
2) ApplicationContext(recommended)

                ex: ApplicationContext contex = new ClassPathXmlApplicationContext(String configFile);

### NOTE - Bean Configuration file contains bean definition
- Bean definitions - target class, dependent class, dependency Injection type

### NOTE - When IOC Container started it will read bean definitions from Bean configuration File and it will perform Dependency Injection 

# First Application Development using spring core module
- Pre-requesites : JDK 1.8v, STS IDE
1) Create Maven project in IDE
2) Add spring Core Dependency in pom.xml file (www.mvnrepository.com)
3) Create Required Java Classes
4) Create Bean Configuration File and configure Bean Definitions
5) Create Main class and start IOC Container to test the application.  
---

Student student =
        context.getBean(Student.class);
```

#### Step 5: Use Bean

```java
student.study();
```

### Flow

Application Start
→ IoC Container Starts
→ Bean Created
→ Bean Stored
→ Bean Retrieved
→ Business Method Called

---

# Interview Revision Sheet

### Q1. What is a Spring Bean?
A Java object managed by the Spring IoC Container.

### Q2. What is IoC?
Control of object creation is transferred from the programmer to Spring.

### Q3. What is Dependency Injection?
Spring injects required dependencies automatically.

### Q4. Difference Between BeanFactory and ApplicationContext?
- BeanFactory → Basic container
- ApplicationContext → Advanced container (recommended)

### Q5. Which method starts Spring Boot?
```java
SpringApplication.run();
```

### Q6. Which annotation creates a Bean?
- `@Component`
- `@Service`
- `@Repository`
- `@Controller`
- `@Bean`

---

# Quick Revision (1 Minute)

- Bean = Object managed by Spring.
- IoC Container = Creates and manages Beans.
- Dependency Injection = Spring provides required objects.
- ApplicationContext = Popular IoC Container.
- Bean Configuration = Defines Bean creation.
- Spring Boot starts IoC using `SpringApplication.run()`.
- `@Component`, `@Service`, `@Repository`, `@Controller` create Beans.
---
## Difference Between BeanFactory and ApplicationContext

| Feature | BeanFactory | ApplicationContext |
|----------|------------|-------------------|
| Definition | Basic IoC Container | Advanced IoC Container |
| Bean Loading | Lazy Loading | Eager Loading (Singleton Beans) |
| Event Handling | Not Supported | Supported |
| Internationalization (i18n) | Not Supported | Supported |
| AOP Support | Limited | Full Support |
| Annotation Support | Limited | Full Support |
| Enterprise Usage | Rarely Used | Widely Used |
| Recommendation | Not Preferred | Preferred |

---

## What is BeanFactory?

BeanFactory is the simplest IoC Container in Spring.

### Key Points
- Creates and manages Beans.
- Uses Lazy Loading.
- Bean is created only when requested using `getBean()`.
- Suitable for small applications.

### Example

```java
BeanFactory factory =
    new XmlBeanFactory(new ClassPathResource("beans.xml"));
```

---

## What is ApplicationContext?

ApplicationContext is an advanced version of BeanFactory.

### Key Points
- Creates and manages Beans.
- Uses Eager Loading by default.
- Supports events, annotations, AOP, and i18n.
- Used in almost all Spring Boot applications.

### Example

```java
ApplicationContext context =
    new ClassPathXmlApplicationContext("beans.xml");
```

---

## Lazy vs Eager Loading

### BeanFactory

Container Starts
→ No Bean Created
→ getBean()
→ Bean Created

### ApplicationContext

Container Starts
→ Bean Created
→ Stored in Container
→ getBean()
→ Bean Returned

---

# Interview Answer

BeanFactory is the basic IoC container that creates Beans lazily when they are requested.

ApplicationContext is an advanced IoC container that creates singleton Beans during startup and provides additional features like event handling, internationalization, annotation support, and AOP.

ApplicationContext is preferred in modern Spring and Spring Boot applications.

---

# Quick Revision

- BeanFactory = Basic Container
- ApplicationContext = Advanced Container
- BeanFactory = Lazy Loading
- ApplicationContext = Eager Loading
- BeanFactory = Limited Features
- ApplicationContext = Enterprise Features
- Spring Boot uses ApplicationContext internally

### NOTE - 
- BeanFactory will follow lazy loading concept that means when we request then only it will create bean object.
- ApplicationContext will follow Eager loading for singleton beans. for prototype beans it will also follow lazy loading
- Spring bean default scope is Singleton.

                1) Eager loading means creating objects for Spring Bean when IOC starts
                2) Lazy Loading means creating object for Spring Bean when we call getBean() method.

# Setter Injection vs Constructor Injection (Bean Configuration File)

## Setter Injection
Spring injects dependency using the setter method after creating the object.

### XML
```xml
<bean id="address" class="com.example.Address"/>
<bean id="student" class="com.example.Student">
    <property name="address" ref="address"/>
</bean>
---

## Constructor Injection
Spring injects dependency through the constructor while creating the object.

### XML
```xml
<bean id="address" class="com.example.Address"/>
<bean id="student" class="com.example.Student">
    <constructor-arg ref="address"/>
</bean>
```

- Uses `<constructor-arg>`
- Dependency injected during object creation
- Suitable for mandatory dependencies

---

## Comparison

| Setter Injection | Constructor Injection |
|---|---|
| Uses setter method | Uses constructor |
| `<property>` | `<constructor-arg>` |
| After object creation | During object creation |
| Optional dependency | Mandatory dependency |
| Mutable object | Can be immutable |
| Less preferred | Recommended in Spring Boot |

---

## Easy Trick to Remember

- **Setter** → **Set Later** → `<property>`
- **Constructor** → **Construct First** → `<constructor-arg>`

---

## Interview Answer

Use **Constructor Injection** when a dependency is mandatory because the object cannot be created without it.

Use **Setter Injection** when a dependency is optional because it can be set after object creation.
              
## Bean scope - 
- scope represents how many objects to be created for a Spring Bean
- In Spring Framework we have below scopes 
        
        1) Singleton --> Default scope (if we dont define anything then that Spring Bean will become Singleton)
        2) Prototype
        3) Request
        4) Session

        - To represent bean scope we will use "scope" attribute

        <bean id = "id" class = "pkg.classname" scope = "singleton|prototype|request|session" />

- Singleton means only one object will be created for the class in IoC Container
- Prototype scope means everytime new object will be created

### NOTE - Request and session scopes are related to Web MVC Module.

## Why Spring bean is by deault Singleton?
- To save memory of JVM 
        ex : Rest controller, Controllers ,Services and DAOs will be considered as singleton in the project

## Autowiring 
- We can perform DI in two ways 
                1) Manual wiring
                2) Auto-Wiring   

- Manual wiring means programmer will inject dependent object into target object using <property/> tag or <constructor-arg/>    

- Autowiring means IoC container will identify dependent bean and it will inject into target object (we no need to use any ref attribute)  
- Autowiring will work based on below modes
        1) byName
        2) byType
        3) constructor
        4) no

### NOTE - Autowiring will not work by default, we have to enable autowiring on target bean like below.

        <bean id = "id" class = "pkg.Classname" auto-wire = "byName|byType|constructor|no />      
        
        1) byName - IoC will identify dependent bean based on bean id or bean name.

        [jiss class ka variable name is matched with another class bean id then that classes obj will be injected and id will always be unique]

        2) byType - IoC will identify dependent bean object based on data type of variable in the target class

        [when there are two with same data type then we will have to give [autowire-candidate="true"] in which class we have to inject the object and in others we have to give autowire-candidate="false"]

        <bean id = "id" class = "pkg.Classname" auto-wire = "byName|byType|constructor|no autowire-candidate="true" />  

        --> If one interface have 2 implementations then there is a chance of getting Ambiguity Problen. To overcome that we need to use 
                autowire-candidate="true" --> [consider this] autowire-candidate="false" --> [dont consider this for autowiring]

        - by using <bean> tag we represent class as a spring bean

        3) constructor - used to perform autowiring by calling target class constructor

- Auto wiring is applicable for reference type variables(not applicable for [primitive types])

### NOTE - as an alternate for "autowire-candidate = true" we can use "primary = true" to consider bean for autowiring 

## Spring Bean life cycle 
- life cycle means starting to ending

        -> Thread Life Cycle
        -> Servlet Life Cycle
        -> JSP Life Cycle
        -> Spring Bean Life Cycle

- Spring Bean object creation and object destruction will be taken care by IOC Container
- Spring Bean Life Cycle will be managed by IOC container
- We can perform some operations using Bean Lifen Cycle Methods

                init() --> initialization logic [this method will be called when the bean object is created]
                destroy() --> destruction logic [when the bean object is removing from the IOC container] (it wont be called if the JVM is stopped without telling the information to IOC that it is going to die )

- Spring bean life cycle methods we can execute in 3 ways -
                1) XML Approach(Declarative)
                2) Progrmmatic approach
                3) Annotations

## Bean life cycle using XML approach 
- init-method -> it represents the method which shoukd be called after bean object created
- destroy-method -> it shopuld be called when bean obj removing from IOC container

## Bean life cycle using Programmatic Approach
- We need to implement PRedefined Interfaces provided by Spring Framework

                1) InitializingBean --> afterPropertiesSet()
                2) DisposableBean --> destroy()

## Bean Life Cycle using Annotation Approach 
- @PostConstruct --> It represents init method
- @PreDestroy --> It represents destroy method 


