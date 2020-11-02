# Java 8
## Predefined Functional Interfaces
### Predicates
* It is a functional interface which has single method  test it accepts single argument and returns a boolean value.
* It is available in the java.util.function package.

```
    interface Predicate<T> {
             public boolean test(T t);
    }
```
* It is a functional interface, so it can refer lamda expression.

> *Write a predicate to check whether the given integer is greater than 10 or not.*

> Actual Signature,
```
Predicate<Integer> p = new Predicate<Integer>() {
            @Override
            public boolean test(Integer I) {
                return I>10 ;
            }
        };
```

> Using Lamda Expression,

```
    Predicate<Integer> p = I->(I>10);  
```

#### Predicate Joining

* We can also join the predicate conditions and get the results by using below methods,
    * p.and(p2);
    * p.or(p2);
    * p.negate();

### Functions
* It is similar to predicates, but functions can return any type.
* But it will return only one value based on the type we provided.
* it contains only one method i.e apply()

> Signature
  
  argument 1 - Processing value
  argument 2 - Return Type
  
```
    Function<String,Integer> function =new Function<String, Integer>() {
            @Override
            public Integer apply(String s) {
                return s.length();
            }
        };
        
```

> Lamda Signature

```
 Function<String,Integer> f1 = s -> s.length();
```

#### Function chaning

* We can combine the Functions and get the results,
  * f1.andThen(f2).apply(); // f1 will execute first then f2 will execute
  * f1.compose(f2).apply();  // first f2 will be applied then f1 will execute
  
 #### Function Interface static method: identity()
 
  * Returns a function that always returns it's input argument.
```
Function<String,String> f2= Function.identity();
```

# Java Questions

1 what is hashCode() and equals()?

* <a href="https://github.com/Snailclimb/JavaGuide/blob/master/docs/java/Java%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.md#129-hashcode%E4%B8%8E-equals">Ref-1</a>
* <a href="https://www.geeksforgeeks.org/internal-working-of-hashmap-java/">Ref-2</a>
* <a href="https://www.java8net.com/2020/01/how-hashmap-works-internally-in-java.html">Ref-3 [MUST READ]</a>

2 what is Autoboxing and Unboxing in Java?
* <a href="https://www.geeksforgeeks.org/autoboxing-unboxing-java/#:~:text=Unboxing%3A%20Converting%20an%20object%20of,of%20the%20corresponding%20primitive%20type.">Ref-1</a>
* <a href="https://beginnersbook.com/2014/09/java-autoboxing-and-unboxing-with-examples/">Ref-2</a>

3 What is constant pools?

4 Why is there only value passing in Java?
* <a href="https://www.journaldev.com/3884/java-is-pass-by-value-and-not-pass-by-reference">Ref-1</a>

5 The difference between overloading and rewriting?

6 Deep copy vs shallow copy?
* <a href= "https://javaconceptoftheday.com/difference-between-shallow-copy-vs-deep-copy-in-java/">Ref-1</a>

### Classes and objects?
7 The difference between object-oriented and process-oriented?

8 Can the Constructor be overridden?

9 The role of a constructor that does nothing and has no parameters in Java?

10 What are the differences between member variables and local variables?

11 Before calling the subclass constructor, the parent class constructor without parameters will be called first. What is its purpose?

12 Encapsulation

13 Inheritance

14 Polymorphism

15  Why is it illegal to call a non-static member within a static method?

16 What is the difference between static methods and instance methods?

17 Summary of common keywords: static, final, this, super?

### Interfaces and abstract classes

18  What is the difference between an interface and an abstract class?

19 Updates of Interface in Java 8 and Java 9?

### Other important knowledge

20 What is the difference between String StringBuffer and StringBuilder? Why is String immutable?

* <a href= "https://www.geeksforgeeks.org/string-vs-stringbuilder-vs-stringbuffer-in-java/#:~:text=Objects%20of%20String%20are%20immutable,needed%2C%20then%20StringBuffer%20is%20used.">Ref-1</a>

21 what are all common methods of Object class?

22 What if some fields do not want to be serialized in Java serialization?

23 Obtaining two commonly used methods for keyboard input?

### Java core technology