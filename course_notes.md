## Spring Framework

----------------------------------------

Video 11:
---------
* What is spring Initializr?

Spring Initializr is a web-based tool provided by the Pivotal Web Service. With the help of Spring Initializr, we can easily generate the structure of the Spring Boot Project. It offers extensible API for creating JVM-based projects.

* what is Spring boot starter?
So just by including this dependency in, we get all these other dependencies.

* start.spring.io
So there's a web application that we can use and select the components that we want in our Spring Boot.

Video 13:
---------

* To compare the branch from one repo to another repo.

git clone repo1
in the same directory git remote add repo2 repo url
git fetch repo2

In intelij we can use the git -> compare branch option two check the changes.

Video 14:
--------

* JPA Entities

@Id
@GeneratedValue(strategy=GenerationType.AUTO)

@manyTomany(mappedBy="author")

Video 15
--------
* Equals and Hashcode

So we want to go in and modify these methods or actually overwrite the methods to provide logic around

the ID property so that if two objects have the same ID, Hibernate and things like sets are going

to consider them the same object.


Video 16
--------

* Spring Data Repostories

Data JPA, what it is doing on underneath the covers is taking care of all the hibernate commands, all

the transactional commands, just about everything that you have to do normally because there is a lot

of ceremonial code.

If you've ever written JDBC code directly, you can understand how much ceremonial code there is.

And this really abstracts it and allows us as developers to go in and just focus on providing business 
functionality


* 	repository extends 
	We are going to extend CrudRepository and that takes to generics. The first property is gonna be the type and the second is going to be the ID value.

	Let's take a quick look at the CrudRepository.
	So this is gonna extend out the repository from a Crud Repository. We are going to get save, save all,
	find by ID, exist by ID, find all, find by ID, account, delete by ID, delete by entity, delete all from
	a list and then delete everything in the repository.
	This also extends out repository as well.



Video 17
--------

* Initialization of some data


And that's gonna implement a command line runner. In a command line runner,
this is an interface that we want to implement.
And this is going to tell Spring. Spring is going to look for instances of this type and want to find
some that's going to go ahead and run them.

@component
 
 Dependency Injection
 

Video 18
--------
 
 We didn't develop any SQL. What's happening under neath the covers I don't think I'm pointing
 this out before his Hibernate is actually generating the SQL DDL statements to go out and create the
 database tables based on our JPA definition.
 
 Hibernate is actually initializing the database, it's generating that SQL statements based on that entities that
 we've created.
 
 Video 19
 --------
 
 And if you go to the URL h2-console, that is where the database console is.
 
 white label error page.This is the standard Spring Boot error page and we're seeing that we're getting a not found status
 404 which is expected at this point.
 
application properties. I'm just going to type H2 and you can see that we do have several settings in the H2 console enable
 is default to false.
 
 > spring.h2.console.enabled=true
 > localhost:8080/h2-conosole

So we are saying that it's available at H2 console. In this here, database available at this jdbc URL.

This is very important.
So that's at H jdbc:h2:mem that means an in-memory database and the schema name is
gonna be testdb. So that's very important to set up. I toggle over to Chrome

 Video 20 Introduction to Spring MVC
 --------
 MVC 
 
  Video  21. Configuring Spring MVC Controllers
  --------
controller method with a request path. That's when Spring gets requests
on a specific path a specific controller method will get invoked.
Now to configure a controller in Spring we're going to agitate the class with the controller annotation.

> @controller

This will tell Spring to manage that class as a Spring Bean and that it is a Spring MVC Controller.

Video  22. Thymeleaf Templates
  --------
  template engine.It's an alternative to Java server pages and there's actually a number of alternatives to JSP.
  
> add dependency