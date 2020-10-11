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
## Verify an Object's Constructor with instanceof

 - JavaScript gives a convenient way to verify this with the instanceof
   operator.

> Create a new instance of the House constructor, calling it myHouse and
> passing a number of bedrooms. Then, use instanceof to verify that it
> is an instance of House.

	    function House(numBedrooms) {
	      this.numBedrooms = numBedrooms;
	    }
	    
	    // Only change code below this line
	    var myHouse = new House(4);
	    
	    myHouse  instanceof House;

## Understand Own Properties

 - Add the own properties of canary to the array ownProps

	    function Bird(name) {
	      this.name = name;
	      this.numLegs = 2;
	    }
	    
	    let canary = new Bird("Tweety");
	    let ownProps = [];
	    // Only change code below this line
	    for(let prop in canary){
	      if(canary.hasOwnProperty(prop)){
	        ownProps.push(prop);
	      }
	    }
	    console.log(ownProps);

## Use Prototype Properties to Reduce Duplicate Code

 - Since all instances automatically have the properties on the
   prototype, think of a prototype as a "recipe" for creating objects.
   Note that the prototype for duck and canary is part of the Bird
   constructor as Bird.prototype. Nearly every object in JavaScript has
   a prototype property which is part of the constructor function that
   created it.

> Add a numLegs property to the prototype of Dog

	    function Dog(name) {
	      this.name = name;
	    }
	    
	    Dog.prototype.numLegs = 4;
	    
	    // Only change code above this line
	    let beagle = new Dog("Snoopy");

## Iterate Over All Properties

> Add all of the own properties of beagle to the array ownProps. Add all
> of the prototype properties of Dog to the array prototypeProps.

    function Dog(name) {
      this.name = name;
    }
    
    Dog.prototype.numLegs = 4;
    
    let beagle = new Dog("Snoopy");
    
    let ownProps = [];
    let prototypeProps = [];
    
    // Only change code below this line
    for(let prop in beagle){
      if(beagle.hasOwnProperty(prop)){
        ownProps.push(prop);
      }else{
        prototypeProps.push(prop);
      }
    }

## Understand the Constructor Property

 - There is a special constructor property located on the object instances duck and beagle that were created in the previous challenges:
 - Since the constructor property can be overwritten (which will be covered in the next two challenges) *it’s generally better to use the instanceof method to check the type of an object*.

> Write a joinDogFraternity function that takes a candidate parameter
> and, using the constructor property, return true if the candidate is a
> Dog, otherwise return false.

    function Dog(name) {
      this.name = name;
    }
    
    // Only change code below this line
    function joinDogFraternity(candidate) {
      if(candidate.constructor === Dog){
        return true;
      }else{
        return false;
      }
    }

## Change the Prototype to a New Object

 - A more efficient way is to set the prototype to a new object that
   already contains the properties. This way, the properties are added
   all at once:

> Add the property numLegs and the two methods eat() and describe() to
> the prototype of Dog by setting the prototype to a new object.

    function Dog(name) {
      this.name = name;
    }
    
    Dog.prototype = {
      // Only change code below this line
      numLegs: 4,
      eat:function(){
        console.log('nom nom nom')
      },
      describe: function(){
        console.log('My Name is ' )
      }
    };

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE0NjkxMDQyMiwxNzE1MzUxNzgxLDE3MD
c1ODk0OTEsLTIwODE0OTc0OTcsNjE4MDA0NzUsNDQyODE5Njk3
LC03OTI2ODM5NTQsLTIwNzYxMzAwOTAsLTEwMTM4ODA5NzUsMT
IzNTU2NjQ4OF19
-->