Spring Fundamentals

What is Spring?
Inversion of Control containers

Alternative to Enterprise Java Beans

POJO based and Interface driven - Any code written for spring can be written without using spring.

Very lightweight and unobtrusive compared to older J2EE methodologies

AOP/Proxies

Built around best practices and patterns

History
Milestone release (2003) -> 1.0 release (2004) -> 1.2.6 Jolt Award (2006) -> 2.0 Release (2006) -> 2.5 Release (2007) -> 3.0 Release (2009) -> 3.1 Release (2011) -> 3.2 Release (2012)

The Problems Spring solves
* Testability
* Maintainability
* Scalability - decouples things
* Complexity
* Business Focus

The Solution
* Removes configuration/ lookup code
* Developers can focus on the business needs
* Code can focus on testing
* Annotation or XML based development

How it works
* Everything is simple POJO
* Essentially a glorified HashMap (but not really)
* Can be used as a Registry

— — — —
ARCHITECTURE AND PROJECT SETUP

Downloading Spring
* 19 jars/sub projects downloaded in the bundle
    * Sources
    * Javadocs

— — — — 
Spring XML Configuration

The first method of configuration and still widely used.

The ApplicationContext.xml
* Doesn’t have to be named ApplicationContext.xml but more of a loose standard
* A simple view of Spring is that it is a Hashmap of objets
    * Objects are name/value pairs
* Although not the intention of Spring, it can be used as a simple Registry
* XML configuration begins with a file named the applicationContext.xml
* There are namespaces that aid in configuration and validation

XML Configuration

* Beans
    * Essentially classes
    * Defining beans replaces using the keyword “new”
    * Define the class, use the interface
* Constructor arguments
    * Used to reference properties of the constructor
* Properties 
    * Getters and setters of the POJO that we are working with
* References
    * References to other beans that we have defined
* Values
    * Basic primitive values that we are setting on our POJO

Beans
Beans need:

* Id or Name
    * Can be used interchangeably
    * Id has to be a valid XML identifier
        * can’t contain special characters, ie “*”, “/“, “.”
    * Name can contain special characters
        * Often doesn’t matter with just Spring, but when building URLs with Spring MVC can be problematic
    * Default No-Args Constructor
        * Setter Injection VS Constructor Injection
    * Class

<bean name=“customerRepository”
   class=“com.pluralsight.repository.HibernateCustomerRepositoryImpl”>
</bean>

Setter VS Constructor Injection

* Setter injection is more common
<bean name="customerService"       class="com.pluralsight.service.CustomerServiceImpl">     <property name="customerRepository" ref="customerRepository"></property> </bean>

* Constructor injection guarantees an object is constructed with all dependencies

Autowiring
* Spring can automatically wire beans together for you
* byType
    * Allows a property to be autowired if exactly one bean of the property type exists in the container. If more than one exists, a fatal exception is thrown, which indicates that you may not use byType autowiring for that bean. If there are no matching beans, nothing happens; the property is not set.
* byName
    * Autowiring by property name. Spring looks for a bean with the same name as the property that needs to be autowired
* constructor
    * Analogous to byType, but applies to constructor arguments. If there is not exactly one bean of the constructor argument type in the container, a fatal error is raised.
* no
    * No autowiring

Autowiring has no noticeable impact on performance.

— — — — 
Spring Annotation Configuration using XML

Second method available for configuring spring.

Component Scanner

* Part of the context namespace

xmlns…

* Two elements needed to configure

