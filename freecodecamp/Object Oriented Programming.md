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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzYxMzAwOTAsLTEwMTM4ODA5NzUsMT
IzNTU2NjQ4OF19
-->