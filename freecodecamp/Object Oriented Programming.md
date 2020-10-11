## Create a Basic JavaScript Object

 - Think about things people see every day, like cars, shops, and birds.
   These are all objects: tangible things people can observe and
   interact with.
 - What are some qualities of these objects? A car has wheels. Shops
   sell items. Birds have wings.
  
 - These qualities, or properties, define what makes up an object.

> Create a dog object with name and numLegs properties, and set them to
> a string and a number, respectively.

    let dog = {
        name: 'Jimmy',
        numLegs: 4
    };
## Create a Method on an Object

 - Objects can have a special type of property, called a method.

> Using the dog object, give it a method called sayLegs. The method
> should return the sentence "This dog has 4 legs."

	    let dog = {
	      name: "Spot",
	      numLegs: 4,
	      sayLegs: function(){
	        return `This dog has ${dog.numLegs} legs.`;
	      }
	    };
	    
	    dog.sayLegs();

## Make Code More Reusable with the this Keyword

 - this is a deep topic, and the above example is only one way to use
   it. In the current context, this refers to the object that the method
   is associated with: duck.
    
 -  It makes the code reusable and easier to read.

> Modify the dog.sayLegs method to remove any references to dog. Use the
> duck example for guidance.

    let dog = {
      name: "Spot",
      numLegs: 4,
      sayLegs: function() {return "This dog has " + this.numLegs + " legs.";}
    };
    
    dog.sayLegs();

## Define a Constructor Function

 - Constructors are functions that create new objects. They define
   properties and behaviors that will belong to the new object. Think of
   them as a blueprint for the creation of new objects.
 - [ ] Constructors are defined with a capitalized name to distinguish
       them from other functions that are not constructors.
 - [ ] Constructors use the keyword this to set properties of the object
       they will create. Inside the constructor, this refers to the new
       object it will create.
 - [ ] Constructors define properties and behaviors instead of returning
       a value as other functions might

> Create a constructor, Dog, with properties name, color, and numLegs
> that are set to a string, a string, and a number, respectively.

    function Dog(){
        this.name  = 'Peter';
        this.color = 'white';
        this.numLegs = 2;
    }

## Extend Constructors to Receive Arguments

>Create another Dog constructor. This time, set it up to take the parameters name and color, and have the property numLegs fixed at 4.
> Then create a new Dog saved in a variable terrier. Pass it two strings
> as arguments for the name and color properties.


    function Dog(name, color) {
        this.name = name;
        this.color = color;
        this.numLegs = 4;
    }
    
    let terrier   = new Dog('Robert','brown');

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc5MjY4Mzk1NCwtMjA3NjEzMDA5MCwtMT
AxMzg4MDk3NSwxMjM1NTY2NDg4XX0=
-->